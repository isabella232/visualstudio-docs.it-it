---
title: Creazione di un'area di controllo, comandi e Impostazioni | Microsoft Docs
description: Informazioni su come estendere l'editor Visual Studio codice con guide alle colonne usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0ae56da8cc30e40048fd454b2f99105d4dcce2dbd9d97e679bfca5be4d4f3b06
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121234824"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Procedura dettagliata: Creare un'area di controllo della visualizzazione, comandi e impostazioni (guide di colonna)
È possibile estendere l'Visual Studio editor di testo/codice con comandi ed effetti di visualizzazione. Questo articolo illustra come iniziare a usare una funzionalità di estensione comune, le guide alle colonne. Le guide alle colonne sono linee visivamente leggere disegnate nella visualizzazione dell'editor di testo per facilitare la gestione del codice in base a larghezze di colonna specifiche. In particolare, il codice formattato può essere importante per gli esempi inclusi in documenti, post di blog o report sui bug.

Questa procedura dettagliata è costituita dai passaggi seguenti:
- Creare un progetto VSIX
- Aggiungere un'area di controllo della visualizzazione dell'editor
- Aggiungere il supporto per il salvataggio e il recupero delle impostazioni (dove disegnare le guide di colonna e il relativo colore)
- Aggiungere comandi (aggiungere/rimuovere guide di colonna, modificarne il colore)
- Posizionare i comandi nel menu Modifica e nei menu di scelta rapida del documento di testo
- Aggiungere il supporto per richiamare i comandi dalla finestra Visual Studio comandi

  È possibile provare una versione della funzionalità guide alle colonne con questa estensione Visual Studio[Gallery](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines).

  > [!NOTE]
  > In questa procedura dettagliata si incolla una grande quantità di codice in alcuni file generati dai modelli di Visual Studio di estensione. Tuttavia, presto questa procedura dettagliata farà riferimento a una soluzione completata in GitHub con altri esempi di estensione. Il codice completato è leggermente diverso perché ha icone di comando reali invece di usare icone generictemplate.

## <a name="get-started"></a>Introduzione
A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="set-up-the-solution"></a>Configurare la soluzione
Prima di tutto, si crea un progetto VSIX, si aggiunge un'area di controllo della visualizzazione dell'editor e quindi si aggiunge un comando (che aggiunge un vspackage per il proprietario del comando). L'architettura di base è la seguente:
- Si dispone di un listener di creazione della visualizzazione testo che crea `ColumnGuideAdornment` un oggetto per ogni vista. Questo oggetto è in ascolto di eventi relativi alla modifica o alle impostazioni della visualizzazione, all'aggiornamento o al ridisegno delle guide di colonna in base alle esigenze.
- È disponibile un oggetto `GuidesSettingsManager` che gestisce la lettura e la scrittura dall'Visual Studio archiviazione delle impostazioni. Gestione impostazioni include anche operazioni per l'aggiornamento delle impostazioni che supportano i comandi utente (aggiunta di colonna, rimozione della colonna, modifica del colore).
- È presente un pacchetto VSIP necessario se si dispone di comandi utente, ma è solo codice boilerplate che inizializza l'oggetto di implementazione dei comandi.
- È presente un oggetto che esegue i comandi utente e collega i gestori di comandi per i comandi `ColumnGuideCommands` dichiarati nel file *con estensione vsct.*

  **VSIX**. Usare **il &#124; Comando Nuovo ...** per creare un progetto. Scegliere il **nodo Extensibility** in **C#** nel riquadro di spostamento sinistro e scegliere **VSIX Project** nel riquadro di destra. Immettere il nome **ColumnGuides e** scegliere **OK** per creare il progetto.

  **Visualizzare l'area di controllo**. Premere il pulsante del puntatore a destra sul nodo del progetto nel Esplora soluzioni. Scegliere il **comando Aggiungi &#124; nuovo elemento ...** per aggiungere un nuovo elemento dell'area di controllo della visualizzazione. Scegliere **Extensibility &#124; Editor** nel riquadro di spostamento a sinistra e scegliere Editor **Viewport Adornment** nel riquadro di destra. Immettere il nome **ColumnGuideAdornment** come nome dell'elemento e scegliere **Aggiungi** per aggiungerlo.

  È possibile vedere che questo modello di elemento ha aggiunto due file al progetto (oltre ai riferimenti e così via): **ColumnGuideAdornment.cs** e **ColumnGuideAdornmentTextViewCreationListener.cs**. I modelli disegnano un rettangolo viola sulla visualizzazione. Nella sezione seguente si modificano un paio di righe nel listener di creazione della vista e si sostituisce il contenuto di **ColumnGuideAdornment.cs.**

  **Comandi**. In **Esplora soluzioni**, premere il pulsante del puntatore a destra sul nodo del progetto. Scegliere il **comando Aggiungi &#124; nuovo elemento ...** per aggiungere un nuovo elemento dell'area di controllo della visualizzazione. Scegliere **Extensibility &#124; VSPackage** nel riquadro di spostamento sinistro e scegliere **Comando** personalizzato nel riquadro di destra. Immettere il nome **ColumnGuideCommands come** nome dell'elemento e scegliere **Aggiungi**. Oltre a diversi riferimenti, l'aggiunta dei comandi e del pacchetto ha aggiunto **anche ColumnGuideCommands.cs**, **ColumnGuideCommandsPackage.cs** e **ColumnGuideCommandsPackage.vsct**. Nella sezione seguente si sostituisce il contenuto del primo e dell'ultimo file per definire e implementare i comandi.

## <a name="set-up-the-text-view-creation-listener"></a>Configurare il listener di creazione della visualizzazione testo
Aprire *ColumnGuideAdornmentTextViewCreationListener.cs* nell'editor. Questo codice implementa un gestore per ogni Visual Studio crea visualizzazioni di testo. Esistono attributi che controllano quando il gestore viene chiamato a seconda delle caratteristiche della visualizzazione.

Il codice deve anche dichiarare un livello di area di controllo. Quando l'editor aggiorna le visualizzazioni, ottiene i livelli dell'area di controllo per la visualizzazione e da che ottiene gli elementi dell'area di controllo. È possibile dichiarare l'ordinamento del livello rispetto ad altri con attributi. Sostituire la riga seguente:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

con queste due righe:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

La riga sostituita si trova in un gruppo di attributi che dichiarano un livello di area di controllo. La prima riga modificata cambia solo quando vengono visualizzate le linee guida della colonna. Disegnare le righe "prima" del testo nella visualizzazione significa che vengono visualizzate dietro o sotto il testo. La seconda riga dichiara che le aree di controllo della guida di colonna sono applicabili alle entità di testo che si adattano alla nozione di documento, ma è possibile dichiarare l'area di controllo, ad esempio, per funzionare solo per il testo modificabile. Sono disponibili altre informazioni nei punti di estensione del [servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)

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

La maggior parte di questo codice crea e analizza il formato delle impostazioni: "RGB( \<int> , , ) , , \<int> \<int> \<int> \<int> ...".  I numeri interi alla fine sono le colonne in base uno in cui si vogliono le guide di colonna. L'estensione guide di colonna acquisisce tutte le impostazioni in una singola stringa di valore dell'impostazione.

Esistono alcune parti del codice che vale la pena evidenziare. La riga di codice seguente ottiene il wrapper Visual Studio gestito per l'archiviazione delle impostazioni. Per la maggior parte, questo astrae il registro Windows, ma questa API è indipendente dal meccanismo di archiviazione.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

L Visual Studio di archiviazione delle impostazioni usa un identificatore di categoria e un identificatore di impostazione per identificare in modo univoco tutte le impostazioni:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Non è necessario usare come `"Text Editor"` nome della categoria. È possibile scegliere qualsiasi elemento.

Le prime funzioni sono i punti di ingresso per modificare le impostazioni. Controllano i vincoli di alto livello, ad esempio il numero massimo di guide consentite.  Chiamano quindi , che `WriteSettings` compone una stringa di impostazioni e imposta la proprietà `GuideLinesConfiguration` . L'impostazione di questa proprietà salva il valore delle impostazioni nell'archivio Visual Studio impostazioni e genera l'evento per aggiornare tutti gli oggetti, ognuno associato `SettingsChanged` a una visualizzazione di `ColumnGuideAdornment` testo.

Esistono un paio di funzioni del punto di ingresso, ad esempio `CanAddGuideline` , che vengono usate per implementare comandi che modificano le impostazioni. Quando Visual Studio i menu, esegue una query sulle implementazioni del comando per verificare se il comando è attualmente abilitato, qual è il nome e così via.  Di seguito viene illustrato come associare questi punti di ingresso per le implementazioni del comando. Per altre informazioni sui comandi, vedere [Estendere menu e comandi](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Implementare la classe ColumnGuideAdornment
Viene `ColumnGuideAdornment` creata un'istanza della classe per ogni visualizzazione di testo che può avere aree di controllo. Questa classe è in ascolto di eventi relativi alla modifica o alla modifica delle impostazioni della visualizzazione e all'aggiornamento o al ridisegno delle guide di colonna in base alle esigenze.

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

Le istanze di questa classe contengono <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> l'oggetto associato e un elenco di oggetti `Line` disegnati sulla visualizzazione.

Il costruttore (chiamato da `ColumnGuideAdornmentTextViewCreationListener` quando Visual Studio nuove viste) crea gli oggetti guida di `Line` colonna.  Il costruttore aggiunge anche gestori per `SettingsChanged` l'evento (definito in `GuidesSettingsManager` ) e gli eventi di visualizzazione e `LayoutChanged` `Closed` .

L'evento viene generato a causa di diversi tipi di modifiche nella `LayoutChanged` vista, incluso Visual Studio crea la vista. Il `OnViewLayoutChanged` gestore chiama per `AddGuidelinesToAdornmentLayer` l'esecuzione. Il codice in determina se è necessario aggiornare le posizioni della riga in base alle modifiche, ad esempio modifiche alle dimensioni del carattere, ai canali di visualizzazione, lo scorrimento orizzontale `OnViewLayoutChanged` e così via. Il codice in fa sì che le linee guida eseere tra i caratteri o subito dopo la colonna di testo che si trova `UpdatePositions` nell'offset di caratteri specificato nella riga di testo.

Ogni volta che le impostazioni `SettingsChanged` cambiano, la funzione ricrea tutti `Line` gli oggetti con tutte le nuove impostazioni. Dopo aver impostato le posizioni della riga, il codice rimuove tutti gli oggetti precedenti dal livello dell'area di controllo `Line` `ColumnGuideAdornment` e aggiunge quelli nuovi.

## <a name="define-the-commands-menus-and-menu-placements"></a>Definire i comandi, i menu e le posizioni dei menu
Può essere necessario dichiarare comandi e menu, inserire gruppi di comandi o menu in vari altri menu e associare gestori di comandi. Questa procedura dettagliata illustra il funzionamento dei comandi in questa estensione, ma per informazioni più dettagliate, vedere [Estendere menu e comandi](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Introduzione al codice
L'estensione Guide colonne mostra la dichiarazione di un gruppo di comandi che appartengono tra loro (aggiunta di colonna, rimozione di colonna, modifica del colore della riga) e quindi inserimento di tale gruppo in un sottomenu del menu di scelta rapida dell'editor.  L'estensione Guide di colonna aggiunge anche i comandi al menu **Principale Modifica,** ma li mantiene invisibili, come illustrato di seguito come modello comune.

L'implementazione dei comandi è in tre parti: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct e ColumnGuideCommands.cs. Il codice generato dai modelli inserisce un comando nel menu **Strumenti** che apre una finestra di dialogo come implementazione. È possibile esaminare come viene implementato nei file con estensione *vsct* e *ColumnGuideCommands.cs* perché è semplice. Sostituire il codice in questi file di seguito.

Il codice del pacchetto contiene dichiarazioni boilerplate necessarie per Visual Studio per individuare che l'estensione offre comandi e per trovare dove posizionare i comandi. Quando il pacchetto viene inizializzato, crea un'istanza della classe di implementazione dei comandi. Per altre informazioni sui pacchetti relativi ai comandi, vedere [Estendere menu e comandi.](../extensibility/extending-menus-and-commands.md)

### <a name="a-common-commands-pattern"></a>Un modello di comandi comuni
I comandi nell'estensione Guide a colonne sono un esempio di modello molto comune in Visual Studio. I comandi correlati vengono inseriti in un gruppo e tale gruppo viene inserito in un menu principale, spesso con " " impostato per rendere `<CommandFlag>CommandWellOnly</CommandFlag>` invisibile il comando.  L'inserimento di comandi nei menu principali (ad esempio **Modifica**) assegna loro nomi utili(ad esempio **Edit.AddColumnGuide),** utili per trovare i comandi quando si riass assegnano tasti di scelta **rapida** in Strumenti Opzioni . È utile anche per ottenere il completamento quando si richiamano i comandi dalla **finestra di comando.**

Si aggiunge quindi il gruppo di comandi ai menu di scelta rapida o ai sottomenu in cui si prevede che l'utente usi i comandi. Visual Studio considera `CommandWellOnly` come un flag di invisibilità solo per i menu principali. Quando si posiziona lo stesso gruppo di comandi in un menu di scelta rapida o in un sottomenu, i comandi sono visibili.

Come parte del modello comune, l'estensione Guide di colonna crea un secondo gruppo che contiene un singolo sottomenu. Il sottomenu contiene a sua volta il primo gruppo con i comandi della guida a quattro colonne. Il secondo gruppo che contiene il sottomenu è l'asset riutilizzabile che si inserisce nei vari menu di scelta rapida, che inserisce un sottomenu in tali menu di scelta rapida.

### <a name="the-vsct-file"></a>File con estensione vsct
Il file *con estensione vsct* dichiara i comandi e la posizione in cui si trova, insieme alle icone e così via. Sostituire il contenuto del file *con estensione vsct* con il codice seguente (illustrato di seguito):

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

**GUID .** Per Visual Studio trovare i gestori di comandi e richiamarli, è necessario assicurarsi che il GUID del pacchetto dichiarato nel file *ColumnGuideCommandsPackage.cs* (generato dal modello di elemento di progetto) corrisponda al GUID del pacchetto dichiarato nel file con estensione *vsct* (copiato in precedenza). Se si usa nuovamente questo codice di esempio, è necessario assicurarsi di avere un GUID diverso in modo da non creare conflitti con altri utenti che potrebbero aver copiato questo codice.

Trovare questa riga in *ColumnGuideCommandsPackage.cs* e copiare il GUID tra virgolette:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Incollare quindi il GUID nel file *con estensione vsct* in modo da avere la riga seguente `Symbols` nelle dichiarazioni:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Anche i GUID per il set di comandi e il file di immagine bitmap devono essere univoci per le estensioni:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Tuttavia, non è necessario modificare il set di comandi e i GUID delle immagini bitmap in questa procedura dettagliata per far funzionare il codice. Il GUID del set di comandi deve corrispondere alla dichiarazione nel file *ColumnGuideCommands.cs,* ma si sostituisce anche il contenuto del file; Pertanto, i GUID corrisponderanno.

Altri GUID nel file *con estensione vsct* identificano i menu preesistenti a cui vengono aggiunti i comandi della guida di colonna, in modo che non cambino mai.

**Sezioni del file**. Il *file con estensione vsct* ha tre sezioni esterne: comandi, posizionamenti e simboli. La sezione dei comandi definisce gruppi di comandi, menu, pulsanti o voci di menu e bitmap per le icone. La sezione relativa ai posizionamenti dichiara la posizione dei gruppi nei menu o altri posizionamenti nei menu preesistnti. La sezione symbols dichiara gli identificatori usati altrove nel file con estensione *vsct,* il che rende il codice *vsct* più leggibile rispetto alla presenza di GUID e numeri esadecimali ovunque.

**Sezione Comandi, definizioni dei gruppi**. La sezione commands definisce prima di tutto i gruppi di comandi. I gruppi di comandi sono comandi visualizzati nei menu con piccole linee grigie che separano i gruppi. Un gruppo può anche riempire un intero sottomenu, come in questo esempio, e in questo caso le linee di separazione grigie non vengono visualizzate. I file con estensione *vsct* dichiarano due gruppi, padre di (menu Principale Modifica) e padre di (menu di scelta rapida `GuidesMenuItemsGroup` `IDM_VS_MENU_EDIT`  `GuidesContextMenuGroup` `IDM_VS_CTXT_CODEWIN` dell'editor di codice).

La seconda dichiarazione di gruppo ha una `0x0600` priorità:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

L'idea è quella di inserire il sottomenu delle guide di colonna alla fine di qualsiasi menu di scelta rapida a cui si aggiunge il gruppo di sottomenu. Tuttavia, non si deve presupporre di conoscere meglio e forzare il sottomenu in modo che sia sempre l'ultimo usando la priorità `0xFFFF` . È necessario provare il numero per vedere dove si trova il sottomenu nei menu di scelta rapida in cui si trova. In questo caso, è sufficientemente alto da poterlo inserire alla fine dei menu, per quanto possibile, ma lascia spazio a un altro utente per progettare l'estensione in modo che sia inferiore rispetto all'estensione delle guide di colonna, se lo si `0x0600` desidera.

**Sezione Comandi, definizione del menu**. Successivamente, la sezione del comando definisce il sottomenu `GuidesSubMenu` , padre di `GuidesContextMenuGroup` . è `GuidesContextMenuGroup` il gruppo aggiunto a tutti i menu di scelta rapida pertinenti. Nella sezione placements il codice inserisce il gruppo con i comandi della guida a quattro colonne in questo sottomenu.

**Sezione Comandi, definizioni dei pulsanti**. La sezione commands definisce quindi le voci di menu o i pulsanti che sono i comandi guide a quattro colonne. `CommandWellOnly`, come illustrato in precedenza, significa che i comandi sono invisibili quando vengono inseriti in un menu principale. Anche due delle dichiarazioni dei pulsanti delle voci di menu (aggiunta della guida e rimozione della guida) hanno un `AllowParams` flag :

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Questo flag abilita, oltre a disporre di posizionamenti del menu principale, il comando per ricevere argomenti quando Visual Studio richiama il gestore comandi.  Se l'utente esegue il comando dalla finestra di comando, l'argomento viene passato al gestore comandi negli argomenti dell'evento.

**Sezioni di comando, definizioni di bitmap**. Infine, la sezione dei comandi dichiara le bitmap o le icone usate per i comandi. Questa sezione è una dichiarazione semplice che identifica la risorsa del progetto ed elenca gli indici in base uno delle icone usate. La sezione symbols del file *con estensione vsct* dichiara i valori degli identificatori usati come indici. Questa procedura dettagliata usa l'elenco di bitmap fornito con il modello di elemento di comando personalizzato aggiunto al progetto.

**Sezione Posizionamenti**. Dopo la sezione commands è la sezione placements. Il primo è il punto in cui il codice aggiunge il primo gruppo descritto in precedenza che contiene i comandi della guida a quattro colonne al sottomenu in cui vengono visualizzati i comandi:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Tutti gli altri posizionamenti aggiungono `GuidesContextMenuGroup` (che contiene `GuidesSubMenu` ) ad altri menu di scelta rapida dell'editor. Quando il codice ha dichiarato `GuidesContextMenuGroup` , era padre del menu di scelta rapida dell'editor di codice. Per questo motivo non viene visualizzata una posizione per il menu di scelta rapida dell'editor di codice.

**Sezione Simboli**. Come indicato in precedenza, la sezione symbols dichiara gli identificatori usati altrove nel file con estensione *vsct,* il che rende il codice *vsct* più leggibile rispetto alla presenza di GUID e numeri esadecimali ovunque. I punti importanti in questa sezione sono che il GUID del pacchetto deve concordare con la dichiarazione nella classe del pacchetto. Inoltre, il GUID del set di comandi deve concordare con la dichiarazione nella classe di implementazione del comando.

## <a name="implement-the-commands"></a>Implementare i comandi
Il file *ColumnGuideCommands.cs* implementa i comandi e collega i gestori. Quando Visual Studio il pacchetto e lo inizializza, il pacchetto chiama a sua volta `Initialize` sulla classe di implementazione dei comandi. L'inizializzazione dei comandi crea semplicemente un'istanza della classe e il costruttore collega tutti i gestori di comandi.

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

**Correzione dei riferimenti** a . A questo punto manca un riferimento. Premere il pulsante del puntatore destro del mouse sul nodo Riferimenti nella Esplora soluzioni. Scegliere il **comando Aggiungi** ... . La **finestra di dialogo** Aggiungi riferimento include una casella di ricerca nell'angolo superiore destro. Immettere "editor" (senza virgolette doppie). Scegliere **l'elemento Microsoft.VisualStudio.Editor** (è necessario selezionare la casella a sinistra dell'elemento, non solo selezionare l'elemento) e scegliere **OK** per aggiungere il riferimento.

**Inizializzazione**.  Quando la classe del pacchetto viene inizializzata, chiama `Initialize` sulla classe di implementazione dei comandi. `ColumnGuideCommands`L'inizializzazione crea un'istanza della classe e salva l'istanza della classe e il riferimento al pacchetto nei membri della classe.

Di seguito viene illustrato uno degli hook del gestore comandi dal costruttore della classe:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Creare un oggetto `OleMenuCommand` . Visual Studio usa il sistema Microsoft Office comandi. Gli argomenti chiave quando si crea un'istanza di sono la funzione che implementa il comando ( ), la funzione da chiamare quando Visual Studio mostra un menu con il comando ( ) e `OleMenuCommand` l'ID `AddColumnGuideExecuted` del `AddColumnGuideBeforeQueryStatus` comando. Visual Studio chiama la funzione di stato della query prima di visualizzare un comando in un menu in modo che  il comando possa renderlo invisibile o disattivato per una particolare visualizzazione del menu (ad esempio, disabilitando Copia se non è presente alcuna selezione), modificarne l'icona o anche modificarne il nome (ad esempio, da Aggiungi qualcosa a Rimuovi qualcosa) e così via. L'ID comando deve corrispondere a un ID di comando dichiarato nel file *con estensione vsct.* Le stringhe per il set di comandi e il comando add delle guide di colonna devono corrispondere tra il file con estensione *vsct* e *columnGuideCommands.cs.*

La riga seguente fornisce assistenza quando gli utenti richiamano il comando tramite la finestra di comando (illustrata di seguito):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Stato della query**. Le funzioni di stato della query e controllano alcune impostazioni (ad esempio il numero massimo di guide o la colonna max) o se è presente una guida di `AddColumnGuideBeforeQueryStatus` `RemoveColumnGuideBeforeQueryStatus` colonna da rimuovere. Abilitano i comandi se le condizioni sono giuste.  Le funzioni di stato delle query devono essere efficienti perché vengono eseguite ogni volta che Visual Studio visualizza un menu e per ogni comando nel menu.

 **Funzione AddColumnGuideExecuted**. La parte interessante dell'aggiunta di una guida è capire la visualizzazione dell'editor corrente e la posizione del punto di inserimento.  In primo luogo, questa funzione chiama , che controlla se è presente un argomento fornito dall'utente negli argomenti dell'evento del gestore comandi e, se non è presente alcun argomento, la funzione controlla la visualizzazione `GetApplicableColumn` dell'editor:

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

`GetCurrentEditorColumn` deve eseguire un po' di analisi per <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> ottenere una visualizzazione del codice.  Se si traccia tramite `GetActiveTextView` , e , è possibile vedere come eseguire questa `GetActiveView` `GetTextViewFromVsTextView` operazione. Il codice seguente è il codice pertinente astratto, a partire dalla selezione corrente, quindi ottenendo il frame della selezione, quindi ottenendo il controllo DocView del frame come , quindi ottenendo un oggetto da IVsTextView, quindi ottenendo un host di visualizzazione e infine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> IWpfTextView:

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

Dopo aver creato un oggetto IWpfTextView, è possibile ottenere la colonna in cui si trova il punto di controllo:

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

Con la colonna corrente in cui l'utente ha fatto clic, il codice chiama semplicemente gestione impostazioni per aggiungere o rimuovere la colonna. Gestione impostazioni genera l'evento su cui tutti gli `ColumnGuideAdornment` oggetti sono in ascolto. Quando viene generato l'evento, questi oggetti aggiornano le visualizzazioni testo associate con le nuove impostazioni della guida di colonna.

## <a name="invoke-command-from-the-command-window"></a>Richiamare il comando dalla finestra di comando
L'esempio di guide di colonna consente agli utenti di richiamare due comandi dalla finestra di comando come forma di estendibilità. Se si usa il **comando &#124; altro Windows &#124; comando,** è possibile visualizzare la finestra di comando. È possibile interagire con la finestra di comando immettendo "edit". Con il completamento del nome del comando e specificando l'argomento 120, si omettono i risultati seguenti:

```csharp
> Edit.AddColumnGuide 120
>
```

Le parti dell'esempio che abilitano questo comportamento si verificano nelle dichiarazioni di file con estensione *vsct,* nel costruttore della classe quando si collegano gestori di comandi e nelle implementazioni del gestore comandi che controllano gli argomenti `ColumnGuideCommands` dell'evento.

È stato visualizzato " " nel file con estensione vsct e le posizioni nel menu principale Modifica anche se i comandi non vengono visualizzati nell'interfaccia utente `<CommandFlag>CommandWellOnly</CommandFlag>` **del** menu Modifica.   Se sono nel menu **principale Modifica, assegna** loro nomi come **Edit.AddColumnGuide.** La dichiarazione del gruppo di comandi che contiene i quattro comandi ha inserito il gruppo **direttamente nel** menu Modifica:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

La sezione buttons ha dichiarato in seguito i `CommandWellOnly` comandi per mantenerli invisibili nel menu principale e dichiararli con `AllowParams` :

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Si è visto che il gestore comandi collega il codice nel `ColumnGuideCommands` costruttore della classe fornisce una descrizione del parametro consentito:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

È stata verificata la presenza di un valore nella funzione prima di verificare la presenza di una colonna corrente nella `GetApplicableColumn` `OleMenuCmdEventArgs` visualizzazione dell'editor:

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
È ora possibile premere **F5 per** eseguire l'estensione Guide di colonna. Aprire un file di testo e usare il menu di scelta rapida dell'editor per aggiungere linee guida, rimuoverle e modificarne il colore. Fare clic nel testo (senza spazi vuoti passati alla fine della riga) per aggiungere una guida di colonna oppure l'editor la aggiunge all'ultima colonna della riga. Se si usa la finestra di comando e si richiamano i comandi con un argomento , è possibile aggiungere guide di colonna ovunque.

Se si vogliono provare diversi posizionamenti dei comandi, modificare i nomi, modificare le icone e così via e si verificano problemi con Visual Studio che mostra il codice più recente nei menu, è possibile reimpostare l'hive sperimentale in cui si esegue il debug. Visualizzare il Windows **Start e** digitare "reset". Cercare ed eseguire il comando Reset **the Next Visual Studio Experimental Instance**. Questo comando pulisce l'hive sperimentale del Registro di sistema di tutti i componenti di estensione. Non pulisce le impostazioni dai componenti, quindi tutte le guide presenti quando si arresta l'hive sperimentale di Visual Studio sono ancora presenti quando il codice legge l'archivio delle impostazioni al successivo avvio.

## <a name="finished-code-project"></a>Progetto di codice completato
Presto sarà disponibile un progetto GitHub di Visual Studio di estendibilità e il progetto completato sarà disponibile. Questo articolo verrà aggiornato in modo da puntare a tale punto quando ciò accade. Il progetto di esempio completato può avere GUID diversi e avrà una striscia di bitmap diversa per le icone dei comandi.

È possibile provare una versione della funzionalità delle guide alle colonne con questa estensione Visual Studio[Gallery.](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)

## <a name="see-also"></a>Vedi anche
- [All'interno dell'editor](../extensibility/inside-the-editor.md)
- [Estendere l'editor e i servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)
- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
- [Estendere menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Aggiungere un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md)
- [Creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)
