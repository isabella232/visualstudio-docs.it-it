---
title: Servizio di linguaggio e punti di estensione dell'editor Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28bb086eb99e4b8128c04f62f9b370eb2eab8fa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703049"
---
# <a name="language-service-and-editor-extension-points"></a>Punti di estensione del servizio di linguaggio e dell'editor
L'editor fornisce punti di estensione che è possibile estendere come parti del componente Managed Extensibility Framework (MEF), inclusa la maggior parte delle funzionalità del servizio di linguaggio. Queste sono le principali categorie di punti di estensione:

- Tipi di contenuto

- Tipi di classificazione e formati di classificazione

- Margini e barre di scorrimento

- Tag

- Ornamenti

- Processori del mouse

- Gestori di rilascio

- Opzioni

- IntelliSense

## <a name="extend-content-types"></a>Estendere i tipi di contenuto
 I tipi di contenuto sono le definizioni dei tipi di testo gestiti dall'editor, ad esempio "text", "code" o "CSharp". Per definire un nuovo tipo di contenuto, <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> dichiarare una variabile del tipo e assegnare un nome univoco al nuovo tipo di contenuto. Per registrare il tipo di contenuto con l'editor, esportarlo con i seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>è il nome del tipo di contenuto.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>è il nome del tipo di contenuto da cui deriva questo tipo di contenuto. Un tipo di contenuto può ereditare da più altri tipi di contenuto.

  Poiché <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> la classe è sealed, è possibile esportarla senza alcun parametro di tipo.

  Nell'esempio seguente vengono illustrati gli attributi di esportazione in una definizione di tipo di contenuto.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 I tipi di contenuto possono essere basati su zero o più tipi di contenuto preesistenti. Questi sono i tipi incorporati:

- Qualsiasi: il tipo di contenuto di base. Padre di tutti gli altri tipi di contenuto.

- Testo: il tipo di base per il contenuto non di proiezione. Eredita da "any".

- Testo normale: per testo non di codice. Eredita da "text".

- Codice: per codice di tutti i tipi. Eredita da "text".

- Inerte: esclude il testo da qualsiasi tipo di gestione. Al testo di questo tipo di contenuto non verrà mai applicata alcuna estensione.

- Proiezione: per il contenuto dei buffer di proiezione. Eredita da "any".

- Intellisense: per il contenuto di IntelliSense. Eredita da "text".

- Sighelp: aiuto firma. Eredita da "intellisense".

- Sighelp-doc: documentazione della guida per la firma. Eredita da "intellisense".

  Di seguito sono riportati alcuni dei tipi di contenuto definiti da Visual Studio e da alcuni linguaggi ospitati in Visual Studio:

- Basic

- C/C++

- ConsoleOutput

- CSharp

- CSS

- Enc

- RisultatiFindResults

- F#

- HTML

- JScript

- XAML

- XML

  Per individuare l'elenco dei tipi <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>di contenuto disponibili, importare l'oggetto , che gestisce la raccolta di tipi di contenuto per l'editor. Il codice seguente importa questo servizio come proprietà.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Per associare un tipo di contenuto <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>a un'estensione di file, utilizzare .

> [!NOTE]
> In Visual Studio le estensioni di <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> file vengono registrate tramite il pacchetto del servizio di linguaggio. Il <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> associa un tipo di contenuto MEF con un'estensione di file che è stata registrata in questo modo.

 Per esportare l'estensione di file nella definizione del tipo di contenuto, è necessario includere gli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: specifica l'estensione del nome file.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: specifica il tipo di contenuto.

  Poiché <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> la classe è sealed, è possibile esportarla senza alcun parametro di tipo.

  Nell'esempio seguente vengono illustrati gli attributi di esportazione di un'estensione di file in una definizione di tipo di contenuto.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 Gestisce <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> le associazioni tra le estensioni di file e i tipi di contenuto.

## <a name="extend-classification-types-and-classification-formats"></a>Estendere i tipi di classificazione e i formati di classificazione
 È possibile utilizzare i tipi di classificazione per definire i tipi di testo per i quali si desidera fornire una gestione diversa (ad esempio, colorando il testo "parola chiave" in blu e il testo "commento" in verde). Definire un nuovo tipo di classificazione <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> dichiarando una variabile di tipo e assegnandole un nome univoco.

 Per registrare il tipo di classificazione con l'editor, esportarlo con i seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del tipo di classificazione.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: il nome del tipo di classificazione da cui eredita questo tipo di classificazione. Tutti i tipi di classificazione ereditano da "text" e un tipo di classificazione può ereditare da più altri tipi di classificazione.

  Poiché <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> la classe è sealed, è possibile esportarla senza alcun parametro di tipo.

  Nell'esempio seguente vengono illustrati gli attributi di esportazione in una definizione di tipo di classificazione.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 L'oggetto <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> fornisce l'accesso alle classificazioni standard. I tipi di classificazione incorporati includono:Built-in classification types include these:

- "text"

- "linguaggio naturale" (deriva da "testo")

- "lingua formale" (deriva da "testo")

- "string" (deriva da "literal")

- "character" (deriva da "letterale")

- "numerico" (deriva da "letterale")

  Un set di tipi <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>di errore diversi ereditada . Includono i seguenti tipi di errore:

- "errore di sintassi"

- "Errore del compilatore"

- "altro errore"

- "avviso"

  Per individuare l'elenco dei tipi <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>di classificazione disponibili, importare l'oggetto , che gestisce l'insieme di tipi di classificazione per l'editor. Il codice seguente importa questo servizio come proprietà.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 È possibile definire una definizione di formato di classificazione per il nuovo tipo di classificazione. Derivare una <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> classe da ed <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>esportarla con il tipo , insieme ai seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del formato.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: il nome visualizzato del formato.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: specifica se il formato viene visualizzato nella pagina **Tipi di carattere e colori** della finestra di dialogo **Opzioni.**

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: la priorità del formato. I valori <xref:Microsoft.VisualStudio.Text.Classification.Priority>validi sono from .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: il nome del tipo di classificazione a cui è mappato questo formato.

  Nell'esempio seguente vengono illustrati gli attributi di esportazione in una definizione di formato di classificazione.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Per individuare l'elenco dei <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>formati disponibili, importare il metodo , che mantiene l'insieme di formati per l'editor. Il codice seguente importa questo servizio come proprietà.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Estendere i margini e le barre di scorrimento
 I margini e le barre di scorrimento sono gli elementi di visualizzazione principali dell'editor oltre alla visualizzazione di testo stessa. È possibile specificare un numero qualsiasi di margini oltre ai margini standard visualizzati intorno alla visualizzazione di testo.

 Implementare <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> un'interfaccia per definire un margine. È inoltre necessario <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> implementare l'interfaccia per creare il margine.

 Per registrare il provider di margini con l'editor, è necessario esportare il provider con i seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del margine.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordine in cui il margine viene visualizzato rispetto agli altri margini.

   Questi sono i margini incorporati:

  - "Barra di scorrimento orizzontale WPF"

  - "Barra di scorrimento verticale WPF"

  - "Margine numero riga Wpf"

    I margini orizzontali di `After="Wpf Horizontal Scrollbar"` cui è presente un attributo di ordine vengono visualizzati `Before ="Wpf Horizontal Scrollbar"` sotto il margine predefinito e i margini orizzontali di cui è presente un attributo di ordine vengono visualizzati sopra il margine predefinito. I margini verticali destro di `After="Wpf Vertical Scrollbar"` cui è riportato un attributo order vengono visualizzati a destra della barra di scorrimento. I margini verticali a sinistra `After="Wpf Line Number Margin"` di cui è presente l'attributo order vengono visualizzati a sinistra del margine del numero di riga (se visibile).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: il tipo di margine (sinistra, destra, in alto o in basso).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "testo" o "codice") per il quale il margine è valido.

  Nell'esempio seguente vengono illustrati gli attributi di esportazione in un provider di margini per un margine visualizzato a destra del margine del numero di riga.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Estendere i tag
 I tag sono un modo per associare i dati a diversi tipi di testo. In molti casi, i dati associati vengono visualizzati come effetto visivo, ma non tutti i tag hanno una presentazione visiva. È possibile definire un tipo <xref:Microsoft.VisualStudio.Text.Tagging.ITag>di tag personalizzato implementando . È inoltre <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> necessario implementare per fornire i tag per <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> un determinato set di intervalli di testo e un per fornire il tagger. È necessario esportare il provider di tagger con i seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "testo" o "codice") per il quale il tag è valido.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: il tipo di tag.

  Nell'esempio seguente vengono illustrati gli attributi di esportazione in un provider di tagger.

\<CodeContentPlaceHolder></CodeContentPlaceHolder> 8 I seguenti tipi di tag sono incorporati:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: associato <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>a un file .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: associato ai tipi di errore.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: associato a un'area di controllo.

  > [!NOTE]
  > Per un esempio <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>di un oggetto , vedere la definizione di HighlightWordTag in [Procedura dettagliata: evidenziazione del testo](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: associate alle aree che possono essere espanse o compresse nella struttura.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definisce lo spazio occupato da un'area di controllo in una visualizzazione di testo. Per ulteriori informazioni sulle aree di controllo di negoziazione dello spazio, vedere la sezione seguente.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: fornisce spaziatura e ridimensionamento automatici per l'area di controllo.

  Per trovare e utilizzare i tag per <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> i <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>buffer e <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> le viste, importare il o il , che forniscono un tipo richiesto. Il codice seguente importa questo servizio come proprietà.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Tag e MarkerFormatDefinitions
 È possibile <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> estendere la classe per definire l'aspetto di un tag. È necessario esportare la <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>classe (come a ) con i seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome utilizzato per fare riferimento a questo formato

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: in questo modo il formato viene visualizzato nell'interfaccia utente

  Nel costruttore si definiscono il nome visualizzato e l'aspetto del tag. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>definisce il colore <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> di riempimento e il colore del bordo. Il <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> è il nome localizzabile della definizione di formato.

  Di seguito è riportato un esempio di definizione di formato:The following is an example of a format definition:

```
[Export(typeof(EditorFormatDefinition))]
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
[UserVisible(true)]
internal class HighlightWordFormatDefinition : MarkerFormatDefinition
{
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
}

```

 Per applicare questa definizione di formato a un tag, fare riferimento al nome impostato nell'attributo name della classe (non il nome visualizzato).

> [!NOTE]
> Per un esempio <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>di un oggetto , vedere la classe HighlightWordFormatDefinition in [Walkthrough: Highlighting Text](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Estendere le aree di adorna
 Gli elementi decorativi definiscono gli effetti visivi che possono essere aggiunti al testo visualizzato in una visualizzazione di testo o alla visualizzazione di testo stessa. È possibile definire la propria area <xref:System.Windows.UIElement>di controllo come qualsiasi tipo di .

 Nella classe di area di <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>controllo, è necessario dichiarare un file . Per registrare il layer dell'area di controllo, esportarlo con i seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome dell'area di controllo.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordine dell'area di controllo rispetto ad altri livelli di area di controllo. La <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> classe definisce quattro livelli predefiniti: Selezione, Struttura, Punto di inserimento e testo.

  Nell'esempio seguente vengono illustrati gli attributi di esportazione in una definizione di layer dell'area di controllo.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 È necessario creare una <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> seconda classe <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> che implementa e gestisce il relativo evento istanze dell'area di controllo. È necessario esportare questa classe con i seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "testo" o "codice") per il quale l'area di controllo è valida.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: il tipo di visualizzazione di testo per cui questa area di controllo è valida. La <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> classe dispone del set di ruoli di visualizzazione di testo predefiniti. Ad esempio, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> viene utilizzato principalmente per le visualizzazioni di testo dei file. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>viene utilizzato per le visualizzazioni di testo che un utente può modificare o spostarsi utilizzando il mouse e la tastiera. Esempi <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> di viste sono la visualizzazione di testo dell'editor e la finestra **di output.**

  Nell'esempio seguente vengono illustrati gli attributi di esportazione nel provider dell'area di controllo.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Un'area di controllo che negozia lo spazio è uno che occupa spazio allo stesso livello del testo. Per creare questo tipo di area di controllo, è <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>necessario definire una classe di tag che eredita da , che definisce la quantità di spazio occupato dall'area di controllo.

 Come per tutte le aree di controllo, è necessario esportare la definizione del livello dell'area di controllo.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Per creare un'istanza dell'area di controllo <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>per la negoziazione dello <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> spazio, è necessario creare una classe che implementa , oltre alla classe che implementa (come con altri tipi di aree di controllo).

 Per registrare il provider di tagger, è necessario esportarlo con i seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "testo" o "codice") per il quale l'area di controllo è valida.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: il tipo di visualizzazione di testo per cui questo tag o area di controllo è valido. La <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> classe dispone del set di ruoli di visualizzazione di testo predefiniti. Ad esempio, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> viene utilizzato principalmente per le visualizzazioni di testo dei file. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>viene utilizzato per le visualizzazioni di testo che un utente può modificare o spostarsi utilizzando il mouse e la tastiera. Esempi <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> di viste sono la visualizzazione di testo dell'editor e la finestra **di output.**

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: il tipo di tag o area di controllo che è stato definito. È necessario aggiungere <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>un secondo per .

  Nell'esempio seguente vengono illustrati gli attributi di esportazione nel provider di tagger per un tag di area di controllo di negoziazione dello spazio.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Estensione dei processori del mouse
 È possibile aggiungere una gestione speciale per l'input del mouse. Creare una classe che <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> eredita da ed eseguire l'override degli eventi del mouse per l'input che si desidera gestire. È inoltre <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> necessario implementare in una seconda <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> classe ed esportarlo con che specifica il tipo di contenuto (ad esempio, "text" o "code") per il quale il gestore del mouse è valido.

 Nell'esempio seguente vengono illustrati gli attributi di esportazione in un provider del processore mouse.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Estendere i gestori di rilascioExtend drop handlers
 È possibile personalizzare il comportamento dei gestori di rilascio <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> per tipi specifici <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> di testo creando una classe che implementa e una seconda classe che implementa per creare il gestore di rilascio. È necessario esportare il gestore di rilascio con gli attributi seguenti:You must export the drop handler together with the following attributes:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: il formato di testo per il quale questo gestore di rilascio è valido. I seguenti formati vengono gestiti in ordine di priorità dal più alto al più basso:

  1. Qualsiasi formato personalizzato

  2. Filedrop

  3. EnhancedMetafile

  4. Waveaudio

  5. Riff

  6. Dif

  7. Impostazioni locali

  8. Tavolozza

  9. Dati penna

  10. Serializable

  11. Collegamento simbolico

  12. Xaml

  13. XamlPackage

  14. Tiff

  15. Bitmap

  16. Dib

  17. MetafileImmagine

  18. CSV

  19. System.String

  20. Formato HTML

  21. Unicodetext

  22. Testo OEM

  23. Testo

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del gestore di rilascio.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordine del gestore di rilascio prima o dopo il gestore di rilascio predefinito. Il gestore di rilascio predefinito per Visual Studio è denominato "DefaultFileDropHandler".

  Nell'esempio seguente vengono illustrati gli attributi di esportazione in un provider del gestore di rilascio.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Estensione delle opzioni dell'editorExtending Editor Options
 È possibile definire opzioni valide solo in un determinato ambito, ad esempio in una visualizzazione di testo. L'editor fornisce questo set di opzioni predefinite: opzioni dell'editor, opzioni di visualizzazione e opzioni di visualizzazione di Windows Presentation Foundation (WPF). Queste opzioni sono <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>disponibili <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>in <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>, , e .

 Per aggiungere una nuova opzione, derivare una classe da una di queste classi di definizione di opzione:To add a new option, derive a class from one of these option definition classes:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  Nell'esempio seguente viene illustrato come esportare una definizione di opzione con un valore booleano.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Estendere IntelliSenseExtend IntelliSense
 IntelliSense è un termine generale per un gruppo di funzionalità che forniscono informazioni sul testo strutturato e il completamento delle istruzioni per esso. Queste funzionalità includono il completamento delle istruzioni, la guida alla firma, le informazioni rapide e le lampadine. Il completamento delle istruzioni consente agli utenti di digitare correttamente una parola chiave del linguaggio o un nome di membro. Guida alla firma visualizza la firma o le firme per il metodo appena digitato dall'utente. Informazioni rapide visualizza una firma completa per un nome di tipo o membro quando il mouse si posa su di esso. La lampadina fornisce azioni aggiuntive per determinati identificatori in determinati contesti, ad esempio la ridenominazione di tutte le occorrenze di una variabile dopo la ridenominazione di un'occorrenza.

 La progettazione di una funzionalità IntelliSense è molto simile in tutti i casi:The design of an IntelliSense feature is much the same in all cases:

- Un *broker* IntelliSense è responsabile del processo complessivo.

- Una *sessione* IntelliSense rappresenta la sequenza di eventi tra l'attivazione del presentatore e il commit o l'annullamento della selezione. La sessione viene in genere attivata da un movimento dell'utente.

- Un *controller* IntelliSense è responsabile di decidere quando la sessione deve iniziare e terminare. Decide inoltre quando le informazioni devono essere impegnate e quando la sessione deve essere annullata.

- *Un'origine* IntelliSense fornisce il contenuto e decide la corrispondenza migliore.

- Un *presentatore* IntelliSense è responsabile della visualizzazione del contenuto.

  Nella maggior parte dei casi, è consigliabile fornire almeno un'origine e un controller. È inoltre possibile fornire un relatore se si desidera personalizzare la visualizzazione.

### <a name="implement-an-intellisense-source"></a>Implementare un'origine IntelliSenseImplement an IntelliSense Source
 Per personalizzare un'origine, è necessario implementare una o più interfacce di origine seguenti:To customize a source, you must implement one (or more) of the following source interfaces:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>è stato deprecato <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>a favore di .

 Inoltre, è necessario implementare un provider dello stesso tipo:In addition, you must implement a provider of the same kind:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>è stato deprecato <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>a favore di .

 È necessario esportare il provider con i seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome dell'origine.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "testo" o "codice") a cui si applica l'origine.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordine in cui deve apparire la sorgente (rispetto ad altre fonti).

- Nell'esempio seguente vengono illustrati gli attributi di esportazione in un provider di origine di completamento.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Per altre informazioni sull'implementazione di origini IntelliSense, vedere le procedure dettagliate seguenti:For more information about implementing IntelliSense sources, see the following walkthroughs:

- [Procedura dettagliata: Visualizzare le descrizioni comandi di informazioni rapideWalkthrough: Display QuickInfo tooltips](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Procedura dettagliata: Visualizza guida firmaWalkthrough: Display Signature Help](../extensibility/walkthrough-displaying-signature-help.md)

- [Procedura dettagliata: Visualizzare il completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implementare un controller IntelliSenseImplement an IntelliSense controller
 Per personalizzare un controller, <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> è necessario implementare l'interfaccia. Inoltre, è necessario implementare un provider di controller con gli attributi seguenti:In addition, you must implement a controller provider together with the following attributes:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del controller.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "testo" o "codice") a cui si applica il controller.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordine in cui il controller deve apparire (rispetto ad altri controller).

  Nell'esempio seguente vengono illustrati gli attributi di esportazione in un provider del controller di completamento.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Per altre informazioni sull'uso dei controller IntelliSense, vedere le procedure dettagliate seguenti:For more information about using IntelliSense controllers, see the following walkthroughs:

- [Procedura dettagliata: Visualizzare le descrizioni comandi di informazioni rapideWalkthrough: Display QuickInfo tooltips](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
