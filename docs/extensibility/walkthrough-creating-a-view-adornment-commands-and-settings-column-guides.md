---
title: Creazione di un'area di visualizzazione, comandi e impostazioni di visualizzazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392c4be60f2285edb986d5ca7a1cf4a2202e03c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905035"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Procedura dettagliata: creare un'area di visualizzazione, comandi e impostazioni (guide di colonna)
È possibile estendere l'editor di testo/codice di Visual Studio con i comandi e gli effetti di visualizzazione. Questo articolo illustra come iniziare a usare una funzionalità di estensione comune, ovvero le guide alle colonne. Le guide di colonna sono linee chiare visive disegnate nella visualizzazione dell'editor di testo, per semplificare la gestione del codice a larghezze di colonna specifiche. In particolare, il codice formattato può essere importante per gli esempi inclusi in documenti, post di Blog o segnalazioni di bug.

Questa procedura dettagliata è costituita dai passaggi seguenti:
- Creare un progetto VSIX
- Aggiungere un'area di visualizzazione dell'editor
- Aggiunta del supporto per il salvataggio e il recupero delle impostazioni (dove creare le guide di colonna e il relativo colore)
- Aggiungere comandi (Aggiungi/Rimuovi guide di colonna, modificarne il colore)
- Inserire i comandi nel menu modifica e nel menu di scelta rapida del documento di testo
- Aggiungere il supporto per richiamare i comandi dalla finestra di comando di Visual Studio

  È possibile provare una versione della funzionalità Guide di colonna con questa[estensione](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)della raccolta di Visual Studio.

  > [!NOTE]
  > In questa procedura dettagliata si incolla una grande quantità di codice in alcuni file generati dai modelli di estensione di Visual Studio. Tuttavia, presto questa procedura dettagliata si riferisce a una soluzione completa su GitHub con altri esempi di estensione. Il codice completato è leggermente diverso in quanto contiene icone di comando reali anziché usare icone generictemplate.

## <a name="get-started"></a>Introduzione
A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="set-up-the-solution"></a>Configurare la soluzione
Innanzitutto, si crea un progetto VSIX, si aggiunge un'area di controllo della visualizzazione dell'editor e quindi si aggiunge un comando (che aggiunge un pacchetto VSPackage per il proprietario del comando). L'architettura di base è la seguente:
- È presente un listener per la creazione di una visualizzazione di testo che crea un `ColumnGuideAdornment` oggetto per ogni visualizzazione. Questo oggetto è in attesa di eventi relativi alla modifica della vista o delle impostazioni modifica, aggiornamento o ridisegno delle guide di colonna in caso di necessità.
- C'è un `GuidesSettingsManager` che gestisce la lettura e la scrittura dall'archiviazione delle impostazioni di Visual Studio. Gestione impostazioni dispone anche di operazioni per l'aggiornamento delle impostazioni che supportano i comandi utente (Aggiungi colonna, Rimuovi colonna, cambia colore).
- Un pacchetto VSIP è necessario se si dispone di comandi utente, ma si tratta solo di codice standard che Inizializza l'oggetto di implementazione dei comandi.
- È presente un `ColumnGuideCommands` oggetto che esegue i comandi utente e associa i gestori di comando per i comandi dichiarati nel file con *estensione vsct* .

  **Progetto VSIX**. Usare il comando **File &#124; nuovo...** per creare un progetto. Scegliere il nodo **estensibilità** in **C#** nel riquadro di spostamento a sinistra e scegliere **progetto VSIX** nel riquadro di destra. Immettere il nome **ColumnGuides** e scegliere **OK** per creare il progetto.

  **Visualizzazione**dell'area di visualizzazione. Premere il pulsante destro del mouse sul nodo del progetto nella Esplora soluzioni. Scegliere il comando **aggiungi &#124; nuovo elemento** per aggiungere un nuovo elemento dell'area di controllo della visualizzazione. Scegliere **Extensibility &#124; editor** nel riquadro di spostamento a sinistra e scegliere l'area di **visualizzazione dell'editor** nel riquadro di destra. Immettere il nome **ColumnGuideAdornment** come nome dell'elemento e scegliere **Aggiungi** per aggiungerlo.

  È possibile vedere che questo modello di elemento ha aggiunto due file al progetto (oltre a riferimenti e così via): **ColumnGuideAdornment.cs** e **ColumnGuideAdornmentTextViewCreationListener.cs**. I modelli traggono un rettangolo viola nella visualizzazione. Nella sezione seguente vengono modificate due righe nel listener di creazione della visualizzazione e viene sostituito il contenuto di **ColumnGuideAdornment.cs**.

  **Comandi**. In **Esplora soluzioni**premere il pulsante destro del mouse sul nodo del progetto. Scegliere il comando **aggiungi &#124; nuovo elemento** per aggiungere un nuovo elemento dell'area di controllo della visualizzazione. Scegliere **Extensibility &#124; VSPackage** nel riquadro di spostamento a sinistra e scegliere **comando personalizzato** nel riquadro di destra. Immettere il nome **ColumnGuideCommands** come nome dell'elemento e scegliere **Aggiungi**. Oltre a diversi riferimenti, l'aggiunta di comandi e pacchetti ha aggiunto anche **ColumnGuideCommands.cs**, **ColumnGuideCommandsPackage.cs**e **ColumnGuideCommandsPackage. vsct**. Nella sezione seguente si sostituisce il contenuto del primo e dell'ultimo file per definire e implementare i comandi.

## <a name="set-up-the-text-view-creation-listener"></a>Configurare il listener per la creazione della visualizzazione testo
Aprire *ColumnGuideAdornmentTextViewCreationListener.cs* nell'editor. Questo codice implementa un gestore per ogni volta che Visual Studio crea visualizzazioni di testo. Esistono attributi che controllano quando viene chiamato il gestore a seconda delle caratteristiche della vista.

Il codice deve anche dichiarare un livello di area di strumenti. Quando l'editor Aggiorna le visualizzazioni, ottiene i livelli di area di visualizzazione e da che ottiene gli elementi dell'area di visualizzazione. È possibile dichiarare l'ordinamento del livello in relazione ad altri utenti con attributi. Sostituire la riga seguente:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

con le due righe seguenti:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

La riga sostituita si trova in un gruppo di attributi che dichiarano un livello di area di strumenti. La prima riga modificata cambia solo quando vengono visualizzate le linee della Guida alle colonne. Il disegno delle righe "prima" del testo nella visualizzazione significa che vengono visualizzate dietro o sotto il testo. La seconda riga dichiara che le aree di lavoro della Guida alle colonne sono applicabili alle entità di testo che soddisfano la nozione di documento, ma è possibile dichiarare l'area di lavoro, ad esempio, solo per il testo modificabile. Sono disponibili altre informazioni nei [punti di estensione dell'editor e dei servizi di linguaggio](../extensibility/language-service-and-editor-extension-points.md)

## <a name="implement-the-settings-manager"></a>Implementare gestione impostazioni
Sostituire il contenuto di *GuidesSettingsManager.cs* con il codice seguente (illustrato di seguito):

```csharp
using Microsoft.VisualStudio.Settings;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Settings;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Media;

namespace ColumnGuides
{
    internal static class GuidesSettingsManager
    {
        // Because my code is always called from the UI thred, this succeeds.
        internal static SettingsManager VsManagedSettingsManager =
            new ShellSettingsManager(ServiceProvider.GlobalProvider);

        private const int _maxGuides = 5;
        private const string _collectionSettingsName = "Text Editor";
        private const string _settingName = "Guides";
        // 1000 seems reasonable since primary scenario is long lines of code
        private const int _maxColumn = 1000;

        static internal bool AddGuideline(int column)
        {
            if (! IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column",
                    "The paramenter must be between 1 and " + _maxGuides.ToString());
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            if (offsets.Count() >= _maxGuides)
                return false;
            // Check for duplicates
            if (offsets.Contains(column))
                return false;
            offsets.Add(column);
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);
            return true;
        }

        static internal bool RemoveGuideline(int column)
        {
            if (!IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column", "The paramenter must be between 1 and 10,000");
            var columns = GuidesSettingsManager.GetColumnOffsets();
            if (! columns.Remove(column))
            {
                // Not present.  Allow user to remove the last column
                // even if they're not on the right column.
                if (columns.Count != 1)
                    return false;

                columns.Clear();
            }
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);
            return true;
        }

        static internal bool CanAddGuideline(int column)
        {
            if (!IsValidColumn(column))
                return false;
            var offsets = GetColumnOffsets();
            if (offsets.Count >= _maxGuides)
                return false;
            return ! offsets.Contains(column);
        }

        static internal bool CanRemoveGuideline(int column)
        {
            if (! IsValidColumn(column))
                return false;
            // Allow user to remove the last guideline regardless of the column.
            // Okay to call count, we limit the number of guides.
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            return offsets.Contains(column) || offsets.Count() == 1;
        }

        static internal void RemoveAllGuidelines()
        {
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);
        }

        private static bool IsValidColumn(int column)
        {
            // zero is allowed (per user request)
            return 0 <= column && column <= _maxColumn;
        }

        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".
        // There can be any number of ints following the RGB part,
        // and each int is a column (char offset into line) where to draw.
        static private string _guidelinesConfiguration;
        static private string GuidelinesConfiguration
        {
            get
            {
                if (_guidelinesConfiguration == null)
                {
                    _guidelinesConfiguration =
                        GetUserSettingsString(
                            GuidesSettingsManager._collectionSettingsName,
                            GuidesSettingsManager._settingName)
                        .Trim();
                }
                return _guidelinesConfiguration;
            }

            set
            {
                if (value != _guidelinesConfiguration)
                {
                    _guidelinesConfiguration = value;
                    WriteUserSettingsString(
                        GuidesSettingsManager._collectionSettingsName,
                        GuidesSettingsManager._settingName, value);
                    // Notify ColumnGuideAdornments to update adornments in views.
                    var handler = GuidesSettingsManager.SettingsChanged;
                    if (handler != null)
                        handler();
                }
            }
        }

        internal static string GetUserSettingsString(string collection, string setting)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);
            return store.GetString(collection, setting, "RGB(255,0,0) 80");
        }

        internal static void WriteUserSettingsString(string key, string propertyName,
                                                     string value)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetWritableSettingsStore(SettingsScope.UserSettings);
            store.CreateCollection(key);
            store.SetString(key, propertyName, value);
        }

        // Persists settings and sets property with side effect of signaling
        // ColumnGuideAdornments to update.
        static private void WriteSettings(Color color, IEnumerable<int> columns)
        {
            string value = ComposeSettingsString(color, columns);
            GuidelinesConfiguration = value;
        }

        private static string ComposeSettingsString(Color color,
                                                    IEnumerable<int> columns)
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();
            if (columnsEnumerator.MoveNext())
            {
                sb.AppendFormat(" {0}", columnsEnumerator.Current);
                while (columnsEnumerator.MoveNext())
                {
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);
                }
            }
            return sb.ToString();
        }

        // Parse a color out of a string that begins like "RGB(255,0,0)"
        static internal Color GuidelinesColor
        {
            get
            {
                string config = GuidelinesConfiguration;
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))
                {
                    int lastParen = config.IndexOf(')');
                    if (lastParen > 4)
                    {
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');

                        if (rgbs.Length >= 3)
                        {
                            byte r, g, b;
                            if (byte.TryParse(rgbs[0], out r) &&
                                byte.TryParse(rgbs[1], out g) &&
                                byte.TryParse(rgbs[2], out b))
                            {
                                return Color.FromRgb(r, g, b);
                            }
                        }
                    }
                }
                return Colors.DarkRed;
            }

            set
            {
                WriteSettings(value, GetColumnOffsets());
            }
        }

        // Parse a list of integer values out of a string that looks like
        // "RGB(255,0,0) 1, 5, 10, 80"
        static internal List<int> GetColumnOffsets()
        {
            var result = new List<int>();
            string settings = GuidesSettingsManager.GuidelinesConfiguration;
            if (String.IsNullOrEmpty(settings))
                return new List<int>();

            if (!settings.StartsWith("RGB("))
                return new List<int>();

            int lastParen = settings.IndexOf(')');
            if (lastParen <= 4)
                return new List<int>();

            string[] columns = settings.Substring(lastParen + 1).Split(',');

            int columnCount = 0;
            foreach (string columnText in columns)
            {
                int column = -1;
                // VS 2008 gallery extension didn't allow zero, so per user request ...
                if (int.TryParse(columnText, out column) && column >= 0)
                {
                    columnCount++;
                    result.Add(column);
                    if (columnCount >= _maxGuides)
                        break;
                }
            }
            return result;
        }

        // Delegate and Event to fire when settings change so that ColumnGuideAdornments
        // can update.  We need nothing special in this event since the settings manager
        // is statically available.
        //
        internal delegate void SettingsChangedHandler();
        static internal event SettingsChangedHandler SettingsChanged;

    }
}

```

La maggior parte di questo codice crea e analizza il formato delle impostazioni: "RGB ( \<int> , \<int> , \<int> ) \<int> , \<int> ,...".  I numeri interi alla fine sono le colonne in base 1 in cui si desiderano le guide alle colonne. L'estensione delle guide di colonna acquisisce tutte le impostazioni in una singola stringa di valore di impostazione.

È opportuno evidenziare alcune parti del codice. La riga di codice seguente ottiene il wrapper gestito di Visual Studio per l'archiviazione delle impostazioni. Nella maggior parte dei casi, il registro di sistema di Windows viene astratto, ma questa API è indipendente dal meccanismo di archiviazione.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

L'archiviazione delle impostazioni di Visual Studio usa un identificatore di categoria e un identificatore dell'impostazione per identificare in modo univoco tutte le impostazioni:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Non è necessario utilizzare `"Text Editor"` come nome della categoria. È possibile scegliere qualsiasi elemento.

Le prime funzioni sono i punti di ingresso per modificare le impostazioni. Verificano vincoli di alto livello come il numero massimo di guide consentite.  Quindi, chiamano `WriteSettings` , che compone una stringa di impostazioni e imposta la proprietà `GuideLinesConfiguration` . Se si imposta questa proprietà, il valore delle impostazioni viene salvato nell'archivio delle impostazioni di Visual Studio e viene generato l' `SettingsChanged` evento per aggiornare tutti gli `ColumnGuideAdornment` oggetti, ognuno associato a una visualizzazione di testo.

Sono disponibili un paio di funzioni del punto di ingresso, ad esempio `CanAddGuideline` , che vengono usate per implementare i comandi che modificano le impostazioni. Quando Visual Studio Visualizza i menu, esegue query sulle implementazioni dei comandi per verificare se il comando è attualmente abilitato, il nome e così via.  Di seguito viene illustrato come associare questi punti di ingresso per le implementazioni dei comandi. Per altre informazioni sui comandi, vedere [estendere i menu e i comandi](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Implementare la classe ColumnGuideAdornment
`ColumnGuideAdornment`Viene creata un'istanza della classe per ogni visualizzazione di testo che può avere aree di visualizzazione. Questa classe è in ascolto degli eventi relativi alla modifica della vista o delle impostazioni e alle guide alle colonne di aggiornamento o di ridisegno secondo necessità.

Sostituire il contenuto di *ColumnGuideAdornment.cs* con il codice seguente (illustrato di seguito):

```csharp
using System;
using System.Windows.Media;
using Microsoft.VisualStudio.Text.Editor;
using System.Collections.Generic;
using System.Windows.Shapes;
using Microsoft.VisualStudio.Text.Formatting;
using System.Windows;

namespace ColumnGuides
{
    /// <summary>
    /// Adornment class, one instance per text view that draws a guides on the viewport
    /// </summary>
    internal sealed class ColumnGuideAdornment
    {
        private const double _lineThickness = 1.0;
        private IList<Line> _guidelines;
        private IWpfTextView _view;
        private double _baseIndentation;
        private double _columnWidth;

        /// <summary>
        /// Creates editor column guidelines
        /// </summary>
        /// <param name="view">The <see cref="IWpfTextView"/> upon
        /// which the adornment will be drawn</param>
        public ColumnGuideAdornment(IWpfTextView view)
        {
            _view = view;
            _guidelines = CreateGuidelines();
            GuidesSettingsManager.SettingsChanged +=
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);
            view.LayoutChanged +=
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);
            _view.Closed += new EventHandler(OnViewClosed);
        }

        void SettingsChanged()
        {
            _guidelines = CreateGuidelines();
            UpdatePositions();
            AddGuidelinesToAdornmentLayer();
        }

        void OnViewClosed(object sender, EventArgs e)
        {
            _view.LayoutChanged -= OnViewLayoutChanged;
            _view.Closed -= OnViewClosed;
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;
        }

        private bool _firstLayoutDone;

        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
        {
            bool fUpdatePositions = false;

            IFormattedLineSource lineSource = _view.FormattedLineSource;
            if (lineSource == null)
            {
                return;
            }
            if (_columnWidth != lineSource.ColumnWidth)
            {
                _columnWidth = lineSource.ColumnWidth;
                fUpdatePositions = true;
            }
            if (_baseIndentation != lineSource.BaseIndentation)
            {
                _baseIndentation = lineSource.BaseIndentation;
                fUpdatePositions = true;
            }
            if (fUpdatePositions ||
                e.VerticalTranslation ||
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)
            {
                UpdatePositions();
            }
            if (!_firstLayoutDone)
            {
                AddGuidelinesToAdornmentLayer();
                _firstLayoutDone = true;
            }
        }

        private static IList<Line> CreateGuidelines()
        {
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });
            IList<Line> result = new List<Line>();
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())
            {
                Line line = new Line()
                {
                    // Use the DataContext slot as a cookie to hold the column
                    DataContext = column,
                    Stroke = lineBrush,
                    StrokeThickness = _lineThickness,
                    StrokeDashArray = dashArray
                };
                result.Add(line);
            }
            return result;
        }

        void UpdatePositions()
        {
            foreach (Line line in _guidelines)
            {
                int column = (int)line.DataContext;
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;
                line.X1 = line.X2;
                line.Y1 = _view.ViewportTop;
                line.Y2 = _view.ViewportBottom;
            }
        }

        void AddGuidelinesToAdornmentLayer()
        {
            // Grab a reference to the adornment layer that this adornment
            // should be added to
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener
            IAdornmentLayer adornmentLayer =
                _view.GetAdornmentLayer("ColumnGuideAdornment");
            if (adornmentLayer == null)
                return;
            adornmentLayer.RemoveAllAdornments();
            // Add the guidelines to the adornment layer and make them relative
            // to the viewport
            foreach (UIElement element in _guidelines)
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,
                                            null, null, element, null);
        }
    }

}
```

Le istanze di questa classe contengono l'oggetto associato <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> e un elenco di `Line` oggetti disegnati nella vista.

Il costruttore (chiamato da `ColumnGuideAdornmentTextViewCreationListener` quando Visual Studio crea nuove visualizzazioni) crea gli oggetti Guida alle colonne `Line` .  Il costruttore aggiunge anche gestori per l' `SettingsChanged` evento (definito in `GuidesSettingsManager` ) e gli eventi di visualizzazione `LayoutChanged` e `Closed` .

L' `LayoutChanged` evento viene generato a causa di diversi tipi di modifiche nella visualizzazione, incluso quando Visual Studio crea la visualizzazione. Il `OnViewLayoutChanged` gestore chiama `AddGuidelinesToAdornmentLayer` per eseguire. Il codice in `OnViewLayoutChanged` determina se è necessario aggiornare le posizioni delle righe in base a modifiche quali le modifiche alle dimensioni del carattere, le grondature delle visualizzazioni, lo scorrimento orizzontale e così via. Il codice in `UpdatePositions` fa in modo che le linee guida disegnino tra i caratteri o subito dopo la colonna di testo che si trova nell'offset carattere specificato nella riga di testo.

Quando le impostazioni cambiano `SettingsChanged` , la funzione ricrea solo tutti gli `Line` oggetti con le nuove impostazioni. Dopo aver impostato le posizioni della riga, il codice rimuove tutti gli `Line` oggetti precedenti dal livello di area di rilievo `ColumnGuideAdornment` e aggiunge quelli nuovi.

## <a name="define-the-commands-menus-and-menu-placements"></a>Definire i comandi, i menu e le opzioni di menu
È possibile dichiarare comandi e menu, inserendo gruppi di comandi o menu in diversi altri menu e associando i gestori di comandi. Questa procedura dettagliata illustra come funzionano i comandi in questa estensione, ma per informazioni più dettagliate, vedere [estendere i menu e i comandi](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Introduzione al codice
L'estensione guide di colonna Mostra la dichiarazione di un gruppo di comandi che appartengono insieme (Aggiungi colonna, Rimuovi colonna, modifica colore linea), quindi inserendo il gruppo in un sottomenu del menu di scelta rapida dell'editor.  L'estensione delle guide di colonna aggiunge anche i comandi al menu principale di **modifica** , ma li mantiene invisibili, descritti come un modello comune di seguito.

L'implementazione dei comandi include tre parti: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage. vsct e ColumnGuideCommands.cs. Il codice generato dai modelli inserisce un comando nel menu **strumenti** che estrae una finestra di dialogo come implementazione. È possibile esaminare il modo in cui viene implementato nei file con *estensione vsct* e *ColumnGuideCommands.cs* , poiché è semplice. Sostituire il codice in questi file di seguito.

Il codice del pacchetto contiene dichiarazioni standard necessarie per l'individuazione da parte di Visual Studio del modo in cui l'estensione offre comandi e per trovare la posizione in cui inserire i comandi. Quando il pacchetto viene inizializzato, crea un'istanza della classe di implementazione dei comandi. Per ulteriori informazioni sui pacchetti relativi ai comandi, vedere [estendere i menu e i comandi](../extensibility/extending-menus-and-commands.md).

### <a name="a-common-commands-pattern"></a>Un modello di comandi comune
I comandi nell'estensione guide di colonna sono un esempio di modello molto comune in Visual Studio. Si inseriscono i comandi correlati in un gruppo e si inserisce tale gruppo in un menu principale, spesso con " `<CommandFlag>CommandWellOnly</CommandFlag>` " impostato per rendere il comando invisibile.  L'inserimento di comandi nei menu principali (ad esempio, **Edit**) fornisce nomi interessanti, ad esempio **Edit. AddColumnGuide**, utili per trovare i comandi quando si riassegnano le combinazioni di tasti nelle **Opzioni degli strumenti**. È utile anche per ottenere il completamento quando si richiamano i comandi dalla **finestra di comando**.

Si aggiunge quindi il gruppo di comandi a menu di scelta rapida o sottomenu in cui si prevede che l'utente usi i comandi. Visual Studio considera `CommandWellOnly` un flag di invisibilità solo per i menu principali. Quando si inserisce lo stesso gruppo di comandi in un menu di scelta rapida o in un sottomenu, i comandi sono visibili.

Come parte del modello comune, l'estensione delle guide di colonna crea un secondo gruppo che contiene un singolo sottomenu. Il sottomenu a sua volta contiene il primo gruppo con i comandi della guida a quattro colonne. Il secondo gruppo che include il sottomenu è l'asset riutilizzabile inserito in diversi menu di scelta rapida, che inserisce un sottomenu nei menu di scelta rapida.

### <a name="the-vsct-file"></a>Il file con estensione vsct
Il file con *estensione vsct* dichiara i comandi e la posizione in cui si trovino, insieme alle icone e così via. Sostituire il contenuto del file con *estensione vsct* con il codice seguente (illustrato di seguito):

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <!--  This is the file that defines the actual layout and type of the commands.
        It is divided in different sections (e.g. command definition, command
        placement, ...), with each defining a specific set of properties.
        See the comment before each section for more details about how to
        use it. -->

  <!--  The VSCT compiler (the tool that translates this file into the binary
        format that VisualStudio will consume) has the ability to run a preprocessor
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so
        it is possible to define includes and macros with the same syntax used
        in C++ files. Using this ability of the compiler here, we include some files
        defining some of the constants that we will use inside the file. -->

  <!--This is the file that defines the IDs for all the commands exposed by
      VisualStudio. -->
  <Extern href="stdidcmd.h"/>

  <!--This header contains the command ids for the menus provided by the shell. -->
  <Extern href="vsshlids.h"/>

  <!--The Commands section is where commands, menus, and menu groups are defined.
      This section uses a Guid to identify the package that provides the command
      defined inside it. -->
  <Commands package="guidColumnGuideCommandsPkg">
    <!-- Inside this section we have different sub-sections: one for the menus, another
    for the menu groups, one for the buttons (the actual commands), one for the combos
    and the last one for the bitmaps used. Each element is identified by a command id
    that is a unique pair of guid and numeric identifier; the guid part of the identifier
    is usually called "command set" and is used to group different command inside a
    logically related group; your package should define its own command set in order to
    avoid collisions with command ids defined by other packages. -->

    <!-- In this section you can define new menu groups. A menu group is a container for
         other menus or buttons (commands); from a visual point of view you can see the
         group as the part of a menu contained between two lines. The parent of a group
         must be a menu. -->
    <Groups>

      <!-- The main group is parented to the edit menu. All the buttons within the group
           have the "CommandWellOnly" flag, so they're actually invisible, but it means
           they get canonical names that begin with "Edit". Using placements, the group
           is also placed in the GuidesSubMenu group. -->
      <!-- The priority 0xB801 is chosen so it goes just after
           IDG_VS_EDIT_COMMANDWELL -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that
           drops the sub menu). The group is parented to
           the context menu for code windows. That takes care of most editors, but it's
           also placed in a couple of other windows using Placements -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />
      </Group>

    </Groups>

    <Menus>
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"
            type="Menu">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />
        <Strings>
          <ButtonText>&Column Guides</ButtonText>
        </Strings>
      </Menu>
    </Menus>

    <!--Buttons section. -->
    <!--This section defines the elements the user can interact with, like a menu command or a button
        or combo box in a toolbar. -->
    <Buttons>
      <!--To define a menu group you have to specify its ID, the parent menu and its
          display priority.
          The command is visible and enabled by default. If you need to change the
          visibility, status, etc, you can use the CommandFlag node.
          You can add more than one CommandFlag node e.g.:
              <CommandFlag>DefaultInvisible</CommandFlag>
              <CommandFlag>DynamicVisibility</CommandFlag>
          If you do not want an image next to your command, remove the Icon node or
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->

      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
              priority="0x0100" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicAddGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Add Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"
              priority="0x0101" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Remove Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"
              priority="0x0103" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicChooseColor" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Column Guide &Color...</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"
              priority="0x0102" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Remove A&ll Columns</ButtonText>
        </Strings>
      </Button>
    </Buttons>

    <!--The bitmaps section is used to define the bitmaps that are used for the
        commands.-->
    <Bitmaps>
      <!--  The bitmap id is defined in a way that is a little bit different from the
            others:
            the declaration starts with a guid for the bitmap strip, then there is the
            resource id of the bitmap strip containing the bitmaps and then there are
            the numeric ids of the elements used inside a button definition. An important
            aspect of this declaration is that the element id
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />
    </Bitmaps>

  </Commands>

  <CommandPlacements>

    <!-- Define secondary placements for our groups -->

    <!-- Place the group containing the three commands in the sub-menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                      priority="0x0100">
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
    </CommandPlacement>

    <!-- The HTML editor context menu, for some reason, redefines its own groups
         so we need to place a copy of our context menu there too. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />
    </CommandPlacement>

    <!-- The HTML context menu in Dev12 changed. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />
    </CommandPlacement>

    <!-- Similarly for Script -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />
    </CommandPlacement>

    <!-- Similarly for ASPX  -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />
    </CommandPlacement>

    <!-- Similarly for the XAML editor context menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x0600">
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />
    </CommandPlacement>

  </CommandPlacements>

  <!-- This defines the identifiers and their values used above to index resources
       and specify commands. -->
  <Symbols>
    <!-- This is the package guid. -->
    <GuidSymbol name="guidColumnGuideCommandsPkg"
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />

    <!-- This is the guid used to group the menu commands together -->
    <GuidSymbol name="guidColumnGuidesCommandSet"
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />
      <IDSymbol name="GuidesSubMenu" value="0x1022" />
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />
    </GuidSymbol>

    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
      <IDSymbol name="bmpPicAddGuide" value="1" />
      <IDSymbol name="bmpPicRemoveGuide" value="2" />
      <IDSymbol name="bmpPicChooseColor" value="3" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />
    </GuidSymbol>

    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />
    </GuidSymbol>
  </Symbols>

</CommandTable>

```

**GUID**. Per consentire a Visual Studio di trovare i gestori di comandi e richiamarli, è necessario verificare che il GUID del pacchetto dichiarato nel file *ColumnGuideCommandsPackage.cs* (generato dal modello di elemento di progetto) corrisponda al GUID del pacchetto dichiarato nel file con *estensione vsct* (copiato dalla precedente). Se si riutilizza questo codice di esempio, è necessario assicurarsi di disporre di un GUID diverso in modo da evitare conflitti con altri utenti che potrebbero aver copiato il codice.

Trovare questa riga in *ColumnGuideCommandsPackage.cs* e copiare il GUID tra virgolette:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Incollare quindi il GUID nel file con *estensione vsct* in modo da avere la riga seguente nelle `Symbols` dichiarazioni:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

I GUID per il set di comandi e il file di immagine bitmap devono essere univoci anche per le estensioni:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Tuttavia, non è necessario modificare i GUID del set di comandi e dell'immagine bitmap in questa procedura dettagliata per far funzionare il codice. Il GUID del set di comandi deve corrispondere alla dichiarazione nel file *ColumnGuideCommands.cs* , ma si sostituisce anche il contenuto del file. i GUID corrisponderanno quindi.

Altri GUID nel file con *estensione vsct* identificano i menu preesistenti a cui vengono aggiunti i comandi della Guida alle colonne, in modo che non vengano mai modificati.

**Sezioni del file**. Il *. vsct* include tre sezioni esterne: comandi, posizionamenti e simboli. La sezione comandi definisce i gruppi di comandi, i menu, i pulsanti o le voci di menu e le bitmap per le icone. La sezione posizioni dichiara la posizione in cui i gruppi vengono visualizzati nei menu o nelle posizioni aggiuntive sui menu preesistenti. La sezione symbols dichiara gli identificatori usati altrove nel file con *estensione vsct* , rendendo il codice *. vsct* più leggibile rispetto alla presenza di GUID e numeri esadecimali ovunque.

**Sezione dei comandi, definizioni dei gruppi**. La sezione commands definisce innanzitutto i gruppi di comandi. I gruppi di comandi sono comandi visualizzati nei menu con linee grigie minime che separano i gruppi. Un gruppo può anche riempire un intero sottomenu, come in questo esempio, e in questo caso non vengono visualizzate le righe di separazione grigio. I file con *estensione vsct* dichiarano due gruppi, l' `GuidesMenuItemsGroup` elemento padre di `IDM_VS_MENU_EDIT` (il menu principale di **modifica** ) e l' `GuidesContextMenuGroup` elemento padre di `IDM_VS_CTXT_CODEWIN` (il menu di scelta rapida dell'editor di codice).

La seconda dichiarazione di gruppo ha una `0x0600` priorità:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

L'idea è quella di inserire il sottomenu Guide colonne alla fine di qualsiasi menu di scelta rapida a cui aggiungere il gruppo sottomenu. Tuttavia, non è necessario presupporre che si conosca meglio e che il sottomenu venga sempre usato per l'ultima volta con una priorità di `0xFFFF` . È necessario provare a usare il numero per vedere dove si trova il sottomenu nei menu di scelta rapida in cui viene inserito. In questo caso, `0x0600` è sufficientemente alto da inserirlo alla fine dei menu per quanto possibile, ma lascia spazio a un altro utente per progettare l'estensione in modo che sia più bassa dell'estensione delle guide di colonne, se auspicabile.

**Sezione commands, menu Definition**. Successivamente, la sezione Command definisce il sottomenu `GuidesSubMenu` , padre di `GuidesContextMenuGroup` . `GuidesContextMenuGroup`È il gruppo aggiunto a tutti i menu di scelta rapida pertinenti. Nella sezione posizionamenti il codice inserisce il gruppo con i comandi della guida a quattro colonne in questo sottomenu.

**Sezione commands, definizioni dei pulsanti**. La sezione commands definisce quindi le voci di menu o i pulsanti che sono i comandi delle guide a quattro colonne. `CommandWellOnly`, illustrato in precedenza, indica che i comandi sono invisibili quando vengono inseriti in un menu principale. Due delle dichiarazioni dei pulsanti delle voci di menu (Aggiungi guida e Rimuovi guida) hanno anche un `AllowParams` flag:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Questo flag Abilita, insieme alla posizione dei menu principale, il comando per ricevere gli argomenti quando Visual Studio richiama il gestore di comandi.  Se l'utente esegue il comando dalla finestra di comando, l'argomento viene passato al gestore del comando negli argomenti dell'evento.

**Sezioni di comando, definizioni di bitmap**. Infine, la sezione commands dichiara le bitmap o le icone usate per i comandi. Questa sezione è una semplice dichiarazione che identifica la risorsa del progetto ed elenca gli indici in base uno delle icone usate. La sezione symbols del file con *estensione vsct* dichiara i valori degli identificatori usati come indici. Questa procedura dettagliata usa la striscia bitmap fornita con il modello di elemento di comando personalizzato aggiunto al progetto.

**Sezione di posizionamento**. Dopo la sezione dei comandi è la sezione posizionamenti. Il primo è il punto in cui il codice aggiunge il primo gruppo discusso sopra che include i comandi della guida a quattro colonne per il sottomenu in cui vengono visualizzati i comandi:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Tutte le altre posizionamenti aggiungono `GuidesContextMenuGroup` (che contiene `GuidesSubMenu` ) ad altri menu di scelta rapida dell'editor. Quando il codice ha dichiarato `GuidesContextMenuGroup` , è stato associato al menu di scelta rapida dell'editor di codice. Questo è il motivo per cui non viene visualizzata una selezione host per il menu di scelta rapida dell'editor di codice.

**Sezione simboli**. Come indicato in precedenza, la sezione symbols dichiara gli identificatori usati in altre parti del file con *estensione vsct* , rendendo il codice *. vsct* più leggibile rispetto alla presenza di GUID e numeri esadecimali ovunque. Gli aspetti importanti di questa sezione sono che il GUID del pacchetto deve accettare la dichiarazione nella classe del pacchetto. Il GUID del set di comandi deve quindi accettare la dichiarazione nella classe di implementazione del comando.

## <a name="implement-the-commands"></a>Implementare i comandi
Il file *ColumnGuideCommands.cs* implementa i comandi e associa i gestori. Quando il pacchetto viene caricato da Visual Studio e inizializzato, il pacchetto chiama a sua volta `Initialize` la classe di implementazione dei comandi. L'inizializzazione dei comandi crea semplicemente un'istanza della classe e il costruttore associa tutti i gestori di comandi.

Sostituire il contenuto del file *ColumnGuideCommands.cs* con il codice seguente (illustrato di seguito):

```csharp
using System;
using System.ComponentModel.Design;
using System.Globalization;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;
using Microsoft.VisualStudio.TextManager.Interop;
using Microsoft.VisualStudio.Text.Editor;
using Microsoft.VisualStudio;

namespace ColumnGuides
{
    /// <summary>
    /// Command handler
    /// </summary>
    internal sealed class ColumnGuideCommands
    {

        const int cmdidAddColumnGuide = 0x0100;
        const int cmdidRemoveColumnGuide = 0x0101;
        const int cmdidChooseGuideColor = 0x0102;
        const int cmdidRemoveAllColumnGuides = 0x0103;

        /// <summary>
        /// Command menu group (command set GUID).
        /// </summary>
        static readonly Guid CommandSet =
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");

        /// <summary>
        /// VS Package that provides this command, not null.
        /// </summary>
        private readonly Package package;

        OleMenuCommand _addGuidelineCommand;
        OleMenuCommand _removeGuidelineCommand;

        /// <summary>
        /// Initializes the singleton instance of the command.
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        public static void Initialize(Package package)
        {
            Instance = new ColumnGuideCommands(package);
        }

        /// <summary>
        /// Gets the instance of the command.
        /// </summary>
        public static ColumnGuideCommands Instance
        {
            get;
            private set;
        }

        /// <summary>
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.
        /// Adds our command handlers for menu (commands must exist in the command
        /// table file)
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        private ColumnGuideCommands(Package package)
        {
            if (package == null)
            {
                throw new ArgumentNullException("package");
            }

            this.package = package;

            // Add our command handlers for menu (commands must exist in the .vsct file)

            OleMenuCommandService commandService =
                this.ServiceProvider.GetService(typeof(IMenuCommandService))
                    as OleMenuCommandService;
            if (commandService != null)
            {
                // Add guide
                _addGuidelineCommand =
                    new OleMenuCommand(AddColumnGuideExecuted, null,
                                       AddColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidAddColumnGuide));
                _addGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_addGuidelineCommand);
                // Remove guide
                _removeGuidelineCommand =
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,
                                       RemoveColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidRemoveColumnGuide));
                _removeGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_removeGuidelineCommand);
                // Choose color
                commandService.AddCommand(
                    new MenuCommand(ChooseGuideColorExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidChooseGuideColor)));
                // Remove all
                commandService.AddCommand(
                    new MenuCommand(RemoveAllGuidelinesExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidRemoveAllColumnGuides)));
            }
        }

        /// <summary>
        /// Gets the service provider from the owner package.
        /// </summary>
        private IServiceProvider ServiceProvider
        {
            get
            {
                return this.package;
            }
        }

        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _addGuidelineCommand.Enabled =
                GuidesSettingsManager.CanAddGuideline(currentColumn);
        }

        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _removeGuidelineCommand.Enabled =
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);
        }

        private int GetCurrentEditorColumn()
        {
            IVsTextView view = GetActiveTextView();
            if (view == null)
            {
                return -1;
            }

            try
            {
                IWpfTextView textView = GetTextViewFromVsTextView(view);
                int column = GetCaretColumn(textView);

                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based
                // positions.
                // However, do not subtract one here since the caret is positioned to the
                // left of
                // the given column and the guidelines are positioned to the right. We
                // want the
                // guideline to line up with the current caret position. e.g. When the
                // caret is
                // at position 1 (zero-based), the status bar says column 2. We want to
                // add a
                // guideline for column 1 since that will place the guideline where the
                // caret is.
                return column;
            }
            catch (InvalidOperationException)
            {
                return -1;
            }
        }

        /// <summary>
        /// Find the active text view (if any) in the active document.
        /// </summary>
        /// <returns>The IVsTextView of the active view, or null if there is no active
        /// document or the
        /// active view in the active document is not a text view.</returns>
        private IVsTextView GetActiveTextView()
        {
            IVsMonitorSelection selection =
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
                                                    as IVsMonitorSelection;
            object frameObj = null;
            ErrorHandler.ThrowOnFailure(
                selection.GetCurrentElementValue(
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));

            IVsWindowFrame frame = frameObj as IVsWindowFrame;
            if (frame == null)
            {
                return null;
            }

            return GetActiveView(frame);
        }

        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)
        {
            if (windowFrame == null)
            {
                throw new ArgumentException("windowFrame");
            }

            object pvar;
            ErrorHandler.ThrowOnFailure(
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));

            IVsTextView textView = pvar as IVsTextView;
            if (textView == null)
            {
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;
                if (codeWin != null)
                {
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
                }
            }
            return textView;
        }

        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)
        {

            if (view == null)
            {
                throw new ArgumentNullException("view");
            }

            IVsUserData userData = view as IVsUserData;
            if (userData == null)
            {
                throw new InvalidOperationException();
            }

            object objTextViewHost;
            if (VSConstants.S_OK
                   != userData.GetData(Microsoft.VisualStudio
                                                .Editor
                                                .DefGuidList.guidIWpfTextViewHost,
                                       out objTextViewHost))
            {
                throw new InvalidOperationException();
            }

            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
            if (textViewHost == null)
            {
                throw new InvalidOperationException();
            }

            return textViewHost.TextView;
        }

        /// <summary>
        /// Given an IWpfTextView, find the position of the caret and report its column
        /// number. The column number is 0-based
        /// </summary>
        /// <param name="textView">The text view containing the caret</param>
        /// <returns>The column number of the caret's position. When the caret is at the
        /// leftmost column, the return value is zero.</returns>
        private static int GetCaretColumn(IWpfTextView textView)
        {
            // This is the code the editor uses to populate the status bar.
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
                textView.Caret.ContainingTextViewLine;
            double columnWidth = textView.FormattedLineSource.ColumnWidth;
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                       / columnWidth));
        }

        /// <summary>
        /// Determine the applicable column number for an add or remove command.
        /// The column is parsed from command arguments, if present. Otherwise
        /// the current position of the caret is used to determine the column.
        /// </summary>
        /// <param name="e">Event args passed to the command handler.</param>
        /// <returns>The column number. May be negative to indicate the column number is
        /// unavailable.</returns>
        /// <exception cref="ArgumentException">The column number parsed from event args
        /// was not a valid integer.</exception>
        private int GetApplicableColumn(EventArgs e)
        {
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
            if (!string.IsNullOrEmpty(inValue))
            {
                int column;
                if (!int.TryParse(inValue, out column) || column < 0)
                    throw new ArgumentException("Invalid column");
                return column;
            }

            return GetCurrentEditorColumn();
        }

        /// <summary>
        /// This function is the callback used to execute a command when the a menu item
        /// is clicked. See the Initialize method to see how the menu item is associated
        /// to this function using the OleMenuCommandService service and the MenuCommand
        /// class.
        /// </summary>
        private void AddColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.AddGuideline(column);
            }
        }

        private void RemoveColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.RemoveGuideline(column);
            }
        }

        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)
        {
            GuidesSettingsManager.RemoveAllGuidelines();
        }

        private void ChooseGuideColorExecuted(object sender, EventArgs e)
        {
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;

            using (System.Windows.Forms.ColorDialog picker =
                new System.Windows.Forms.ColorDialog())
            {
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,
                                                             color.B);
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)
                {
                    GuidesSettingsManager.GuidelinesColor =
                        System.Windows.Media.Color.FromRgb(picker.Color.R,
                                                           picker.Color.G,
                                                           picker.Color.B);
                }
            }
        }

    }
}

```

**Correzione di riferimenti**. A questo punto manca un riferimento. Premere il pulsante destro del mouse sul nodo riferimenti nel Esplora soluzioni. Scegliere il comando **Add...** . Nella finestra di dialogo **Aggiungi riferimento** è presente una casella di ricerca nell'angolo superiore destro. Immettere "Editor" (senza le virgolette doppie). Scegliere l'elemento **Microsoft. VisualStudio. Editor** (è necessario selezionare la casella a sinistra dell'elemento, non solo selezionare l'elemento) e scegliere **OK** per aggiungere il riferimento.

**Inizializzazione**.  Quando la classe del pacchetto viene inizializzata, chiama `Initialize` sulla classe di implementazione Commands. L' `ColumnGuideCommands` inizializzazione crea un'istanza della classe e salva l'istanza della classe e il riferimento al pacchetto nei membri della classe.

Esaminiamo uno degli hook del gestore di comandi dal costruttore della classe:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Viene creato un oggetto `OleMenuCommand` . Visual Studio usa il sistema di comando Microsoft Office. Gli argomenti chiave quando si crea un'istanza di `OleMenuCommand` sono la funzione che implementa il comando ( `AddColumnGuideExecuted` ), la funzione da chiamare quando Visual Studio Visualizza un menu con il comando ( `AddColumnGuideBeforeQueryStatus` ) e l'ID di comando. Visual Studio chiama la funzione di stato della query prima di visualizzare un comando in un menu, in modo che il comando possa renderlo invisibile o disattivato per una particolare visualizzazione del menu (ad esempio, la disabilitazione della **copia** se non è presente alcuna selezione), modificare la relativa icona o addirittura modificare il nome (ad esempio, da Aggiungi qualcosa per rimuovere qualcosa) e così via. L'ID del comando deve corrispondere a un ID di comando dichiarato nel file con *estensione vsct* . Le stringhe per il set di comandi e il comando di aggiunta delle guide di colonna devono corrispondere tra il file con estensione *vsct* e *ColumnGuideCommands.cs*.

La riga seguente fornisce assistenza per il momento in cui gli utenti richiamano il comando tramite la finestra di comando (illustrata di seguito):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Stato della query**. Le funzioni di stato della query `AddColumnGuideBeforeQueryStatus` e `RemoveColumnGuideBeforeQueryStatus` controllano alcune impostazioni, ad esempio il numero massimo di guide o la colonna Max, oppure se è presente una guida a colonne da rimuovere. Abilitano i comandi se le condizioni sono corrette.  Le funzioni di stato delle query devono essere efficienti perché vengono eseguite ogni volta che Visual Studio Visualizza un menu e per ogni comando nel menu.

 **Funzione AddColumnGuideExecuted**. La parte interessante dell'aggiunta di una guida consiste nell'individuare la visualizzazione dell'editor corrente e la posizione del punto di inserimento.  In primo luogo, questa funzione chiama `GetApplicableColumn` , che verifica se è presente un argomento fornito dall'utente negli argomenti dell'evento del gestore comando e se non è presente alcun valore, la funzione controlla la visualizzazione dell'Editor:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

    return GetCurrentEditorColumn();
}

```

`GetCurrentEditorColumn` deve approfondire un po' per ottenere una <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> visualizzazione del codice.  Se si tracciano `GetActiveTextView` , `GetActiveView` e `GetTextViewFromVsTextView` , è possibile vedere come eseguire questa operazione. Il codice seguente è il codice pertinente astratto, a partire dalla selezione corrente, ottenendo quindi il frame della selezione, ottenendo il DocView del frame come <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> , ottenendo un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> da IVsTextView, ottenendo quindi un host di visualizzazione e infine IWpfTextView:

```csharp
   IVsMonitorSelection selection =
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
           as IVsMonitorSelection;
   object frameObj = null;

ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,
                                out frameObj));

   IVsWindowFrame frame = frameObj as IVsWindowFrame;
   if (frame == null)
       <<do nothing>>;

...
   object pvar;
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,
                                                  out pvar));

   IVsTextView textView = pvar as IVsTextView;
   if (textView == null)
   {
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;
       if (codeWin != null)
       {
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
       }
   }

...
   if (textView == null)
       <<do nothing>>

   IVsUserData userData = textView as IVsUserData;
   if (userData == null)
       <<do nothing>>

   object objTextViewHost;
   if (VSConstants.S_OK
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList
                                                            .guidIWpfTextViewHost,
                                out objTextViewHost))
   {
       <<do nothing>>
   }

   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
   if (textViewHost == null)
       <<do nothing>>

   IWpfTextView textView = textViewHost.TextView;

```

Quando si dispone di un IWpfTextView, è possibile ottenere la colonna in cui si trova il punto di inserimento:

```csharp
private static int GetCaretColumn(IWpfTextView textView)
{
    // This is the code the editor uses to populate the status bar.
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
        textView.Caret.ContainingTextViewLine;
    double columnWidth = textView.FormattedLineSource.ColumnWidth;
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                / columnWidth));
}

```

Con la colonna corrente in cui l'utente ha fatto clic, il codice chiama semplicemente su Gestione impostazioni per aggiungere o rimuovere la colonna. Gestione impostazioni genera l'evento in cui tutti `ColumnGuideAdornment` gli oggetti sono in ascolto. Quando viene generato l'evento, questi oggetti aggiornano le visualizzazioni di testo associate con le nuove impostazioni della Guida alle colonne.

## <a name="invoke-command-from-the-command-window"></a>Richiama comando dalla finestra di comando
L'esempio guide per le colonne consente agli utenti di richiamare due comandi dalla finestra di comando sotto forma di estendibilità. Se si usa il comando **visualizza &#124; altre finestre &#124; finestra di comando** , è possibile visualizzare la finestra di comando. È possibile interagire con la finestra di comando immettendo "Edit." e con il completamento del nome del comando e specificando l'argomento 120, si ottiene il risultato seguente:

```csharp
> Edit.AddColumnGuide 120
>
```

Le parti dell'esempio che consentono questo comportamento si trovano nelle dichiarazioni di file con *estensione vsct* , nel `ColumnGuideCommands` costruttore della classe quando si collegano i gestori di comandi e nelle implementazioni del gestore di comando che controllano gli argomenti dell'evento.

È stato visualizzato " `<CommandFlag>CommandWellOnly</CommandFlag>` " nel file con *estensione vsct* , oltre a posizionamenti nel menu **modifica** principale anche se i comandi non vengono visualizzati nell'interfaccia utente del menu **modifica** . Se sono presenti nel menu di **modifica** principale, i nomi sono like **Edit. AddColumnGuide**. La dichiarazione del gruppo di comandi che include i quattro comandi posiziona il gruppo direttamente nel menu **modifica** :

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

Nella sezione dei pulsanti sono stati successivamente dichiarati i comandi `CommandWellOnly` per mantenerli invisibili nel menu principale e dichiararli con `AllowParams` :

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Si è visto che il codice di hook del gestore di comando nel `ColumnGuideCommands` costruttore della classe ha fornito una descrizione del parametro consentito:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Si è visto che la `GetApplicableColumn` funzione verifica la presenza `OleMenuCmdEventArgs` di un valore prima di controllare la visualizzazione dell'editor per una colonna corrente:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

```

## <a name="try-your-extension"></a>Provare l'estensione
È ora possibile premere **F5** per eseguire l'estensione delle guide di colonna. Aprire un file di testo e utilizzare il menu di scelta rapida dell'editor per aggiungere linee guida, rimuoverle e modificarne il colore. Fare clic nel testo (non lo spazio vuoto passato alla fine della riga) per aggiungere una guida a colonne oppure l'editor lo aggiunge all'ultima colonna della riga. Se si usa la finestra di comando e si richiamano i comandi con un argomento, è possibile aggiungere guide di colonna in qualsiasi punto.

Se si vuole provare diverse parti del comando, modificare i nomi, modificare le icone e così via, e si verificano problemi con Visual Studio che mostra il codice più recente nei menu, è possibile reimpostare l'hive sperimentale in cui si esegue il debug. Visualizzare il **menu Start di Windows** e digitare "reset". Cercare ed eseguire il comando, **reimpostare la successiva istanza sperimentale di Visual Studio**. Questo comando pulisce l'hive del registro di sistema sperimentale di tutti i componenti di estensione. Non pulisce le impostazioni dai componenti, quindi tutte le guide disponibili quando si arresta l'hive sperimentale di Visual Studio sono ancora presenti quando il codice legge l'archivio impostazioni all'avvio successivo.

## <a name="finished-code-project"></a>Progetto di codice terminato
Ci sarà presto un progetto GitHub di esempi di estendibilità di Visual Studio e il progetto completato sarà disponibile. Questo articolo verrà aggiornato in modo che punti quando si verifica. Il progetto di esempio completato può avere GUID diversi e avrà una striscia di bitmap diversa per le icone dei comandi.

È possibile provare una versione della funzionalità Guide di colonna con questa[estensione](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)della raccolta di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [All'interno dell'editor](../extensibility/inside-the-editor.md)
- [Estendere l'editor e i servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)
- [Punti di estensione Editor e servizio di linguaggio](../extensibility/language-service-and-editor-extension-points.md)
- [Estendi menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Aggiungere un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md)
- [Creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)
