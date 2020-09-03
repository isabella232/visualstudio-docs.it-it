---
title: Punti di estensione del servizio di linguaggio e dell'editor | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703049"
---
# <a name="language-service-and-editor-extension-points"></a>Punti di estensione Editor e servizio di linguaggio
L'editor fornisce punti di estensione che è possibile estendere come parti del componente Managed Extensibility Framework (MEF), inclusa la maggior parte delle funzionalità del servizio di linguaggio. Di seguito sono riportate le principali categorie di punti di estensione:

- Tipi di contenuto

- Tipi di classificazione e formati di classificazione

- Margini e barre di scorrimento

- Tag

- Aree

- Processori mouse

- Gestori di rilascio

- Opzioni

- IntelliSense

## <a name="extend-content-types"></a>Estendi tipi di contenuto
 I tipi di contenuto sono le definizioni dei tipi di testo gestiti dall'editor, ad esempio, "Text", "code" o "CSharp". Definire un nuovo tipo di contenuto dichiarando una variabile del tipo <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> e assegnando al nuovo tipo di contenuto un nome univoco. Per registrare il tipo di contenuto con l'editor, esportarlo insieme ai seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> nome del tipo di contenuto.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> nome del tipo di contenuto da cui viene derivato questo tipo di contenuto. Un tipo di contenuto può ereditare da più tipi di contenuto.

  Poiché la <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> classe è sealed, è possibile esportarla senza parametri di tipo.

  Nell'esempio seguente vengono illustrati gli attributi Export in una definizione di tipo di contenuto.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 I tipi di contenuto possono essere basati su zero o più tipi di contenuto preesistenti. Questi sono i tipi predefiniti:

- Any: tipo di contenuto di base. Elemento padre di tutti gli altri tipi di contenuto.

- Text: tipo di base per il contenuto non di proiezione. Eredita da "any".

- Testo normale: per il testo non di codice. Eredita da "Text".

- Code: per il codice di tutti i tipi. Eredita da "Text".

- Inerti: esclude il testo da qualsiasi tipo di gestione. Al testo di questo tipo di contenuto non verrà mai applicata alcuna estensione.

- Proiezione: per il contenuto dei buffer di proiezione. Eredita da "any".

- IntelliSense: per il contenuto di IntelliSense. Eredita da "Text".

- Sighelp: Guida alla firma. Eredita da "IntelliSense".

- Sighelp-doc: documentazione della Guida di firma. Eredita da "IntelliSense".

  Questi sono alcuni dei tipi di contenuto definiti da Visual Studio e alcuni dei linguaggi ospitati in Visual Studio:

- Basic

- C/C++

- ConsoleOutput

- CSharp

- CSS

- ENC

- FindResults

- F#

- HTML

- JScript

- XAML

- XML

  Per individuare l'elenco dei tipi di contenuto disponibili, importare <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> , che mantiene la raccolta di tipi di contenuto per l'editor. Il codice seguente importa questo servizio come proprietà.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Per associare un tipo di contenuto a un'estensione del nome di file, utilizzare <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> .

> [!NOTE]
> In Visual Studio le estensioni dei nomi di file vengono registrate usando <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> in un pacchetto del servizio di linguaggio. <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>Associa un tipo di contenuto MEF a un'estensione di file registrata in questo modo.

 Per esportare l'estensione del nome file nella definizione del tipo di contenuto, è necessario includere gli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: specifica l'estensione del nome file.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: specifica il tipo di contenuto.

  Poiché la <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> classe è sealed, è possibile esportarla senza parametri di tipo.

  Nell'esempio seguente viene illustrato come esportare gli attributi in un'estensione di file in una definizione di tipo di contenuto.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>Gestisce le associazioni tra le estensioni dei nomi di file e i tipi di contenuto.

## <a name="extend-classification-types-and-classification-formats"></a>Estendi tipi di classificazione e formati di classificazione
 È possibile utilizzare i tipi di classificazione per definire i tipi di testo per i quali si desidera fornire una gestione diversa, ad esempio colorando il testo "keyword" blu e il testo "comment" verde. Definire un nuovo tipo di classificazione dichiarando una variabile di tipo <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> e assegnando un nome univoco.

 Per registrare il tipo di classificazione con l'editor, esportarlo insieme ai seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome del tipo di classificazione.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: nome del tipo di classificazione da cui questo tipo di classificazione eredita. Tutti i tipi di classificazione ereditano da "Text" e un tipo di classificazione può ereditare da più tipi di classificazione.

  Poiché la <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> classe è sealed, è possibile esportarla senza parametri di tipo.

  Nell'esempio seguente vengono illustrati gli attributi Export in una definizione del tipo di classificazione.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>Consente di accedere alle classificazioni standard. I tipi di classificazione predefiniti includono i seguenti:

- "text"

- "linguaggio naturale" (deriva da "testo")

- "linguaggio formale" (deriva da "testo")

- "String" (deriva da "Literal")

- "character" (deriva da "Literal")

- "Numerical" (deriva da "Literal")

  Un set di diversi tipi di errore eredita da <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> . Includono i tipi di errore seguenti:

- "errore di sintassi"

- "errore del compilatore"

- "altro errore"

- avviso

  Per individuare l'elenco dei tipi di classificazione disponibili, importare <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> , che mantiene la raccolta di tipi di classificazione per l'editor. Il codice seguente importa questo servizio come proprietà.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 È possibile definire una definizione del formato di classificazione per il nuovo tipo di classificazione. Derivare una classe da <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> ed esportarla con il tipo <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> , insieme agli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome del formato.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: nome visualizzato del formato.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: specifica se il formato viene visualizzato nella pagina **tipi di carattere e colori** della finestra di dialogo **Opzioni** .

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: priorità del formato. I valori validi sono da <xref:Microsoft.VisualStudio.Text.Classification.Priority> .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: nome del tipo di classificazione a cui viene eseguito il mapping del formato.

  Nell'esempio seguente vengono illustrati gli attributi Export in una definizione di formato di classificazione.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Per individuare l'elenco dei formati disponibili, importare la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> , che mantiene la raccolta di formati per l'editor. Il codice seguente importa questo servizio come proprietà.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Estendi margini e barre di scorrimento
 I margini e le barre di scorrimento sono gli elementi di visualizzazione principali dell'editor, oltre alla visualizzazione di testo. È possibile specificare un numero qualsiasi di margini oltre ai margini standard visualizzati intorno alla visualizzazione di testo.

 Implementare un' <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interfaccia per definire un margine. È inoltre necessario implementare l' <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfaccia per creare il margine.

 Per registrare il provider di margini nell'editor, è necessario esportare il provider insieme ai seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome del margine.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: ordine in cui viene visualizzato il margine rispetto agli altri margini.

   I margini predefiniti sono i seguenti:

  - "Barra di scorrimento orizzontale WPF"

  - "Barra di scorrimento verticale WPF"

  - "Margine del numero di riga WPF"

    I margini orizzontali che hanno un attributo order di `After="Wpf Horizontal Scrollbar"` vengono visualizzati al di sotto del margine predefinito e i margini orizzontali che hanno un attributo order di `Before ="Wpf Horizontal Scrollbar"` vengono visualizzati sopra il margine predefinito. I margini verticali a destra che hanno un attributo order di `After="Wpf Vertical Scrollbar"` vengono visualizzati a destra della barra di scorrimento. I margini verticali a sinistra con un attributo order di `After="Wpf Line Number Margin"` vengono visualizzati a sinistra del margine del numero di riga (se visibile).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: tipo di margine (a sinistra, a destra, in alto o in basso).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: tipo di contenuto (ad esempio, "testo" o "codice") per cui il margine è valido.

  Nell'esempio seguente vengono illustrati gli attributi di esportazione in un provider di margini per un margine visualizzato a destra del margine del numero di riga.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Estendi Tag
 I tag sono un modo per associare i dati a diversi tipi di testo. In molti casi, i dati associati vengono visualizzati come effetti visivi, ma non tutti i tag hanno una presentazione visiva. È possibile definire un tipo di tag personalizzato implementando <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . È inoltre necessario implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> per fornire i tag per un determinato set di intervalli di testo e un oggetto <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> per fornire il tag. È necessario esportare il provider di tag insieme ai seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: tipo di contenuto (ad esempio, "testo" o "codice") per il quale il tag è valido.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: tipo di tag.

  Nell'esempio seguente vengono illustrati gli attributi di esportazione in un provider di tag.

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> i seguenti tipi di tag sono incorporati:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: associato a <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: associato ai tipi di errore.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: associato a un'area di strumenti.

  > [!NOTE]
  > Per un esempio di <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> , vedere la definizione di HighlightWordTag in [procedura dettagliata: evidenziazione del testo](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: associato a aree che possono essere espanse o compresse nella struttura.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definisce lo spazio occupato da un'area di visualizzazione in una visualizzazione di testo. Per ulteriori informazioni sulle aree di strumenti di negoziazione dello spazio, vedere la sezione seguente.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: fornisce la spaziatura automatica e il ridimensionamento per l'area di ridimensionamento.

  Per trovare e usare tag per buffer e visualizzazioni, importare <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> o <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> , che forniscono un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> del tipo richiesto. Il codice seguente importa questo servizio come proprietà.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Tag e MarkerFormatDefinitions
 È possibile estendere la <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> classe per definire l'aspetto di un tag. È necessario esportare la classe (come <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> ) con gli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome utilizzato per fare riferimento a questo formato

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: il formato verrà visualizzato nell'interfaccia utente

  Nel costruttore è possibile definire il nome visualizzato e l'aspetto del tag. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> definisce il colore di riempimento e <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> definisce il colore del bordo. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>È il nome localizzabile della definizione del formato.

  Di seguito è riportato un esempio di definizione di formato:

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

 Per applicare questa definizione di formato a un tag, fare riferimento al nome impostato nell'attributo Name della classe (non il nome visualizzato).

> [!NOTE]
> Per un esempio di <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> , vedere la classe HighlightWordFormatDefinition in [procedura dettagliata: evidenziazione del testo](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Estendi aree di strumenti
 Gli elementi decorativi definiscono gli effetti visivi che è possibile aggiungere al testo visualizzato in una visualizzazione di testo o nella visualizzazione di testo. È possibile definire un'area di lavoro personalizzata come qualsiasi tipo di <xref:System.Windows.UIElement> .

 Nella classe Adornment è necessario dichiarare un oggetto <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> . Per registrare il livello di area di lavoro, esportarlo insieme ai seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome dell'area di strumenti.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: ordinamento dell'area di abbellimento rispetto ad altri livelli di area di strumenti. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> definisce quattro livelli predefiniti: selezione, struttura, punto di inserimento e testo.

  Nell'esempio seguente vengono illustrati gli attributi Export in una definizione del livello di area di strumenti.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 È necessario creare una seconda classe che implementi <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> e gestisca l' <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> evento creando un'istanza dell'area di strumenti. È necessario esportare questa classe insieme ai seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "testo" o "codice") per cui l'area di l'area di l'area di testo è valida.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: tipo di visualizzazione di testo per cui l'area di visualizzazione è valida. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> dispone del set di ruoli della visualizzazione di testo predefiniti. Ad esempio, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> viene utilizzato principalmente per le visualizzazioni di testo dei file. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> viene usato per le visualizzazioni di testo che un utente può modificare o spostarsi usando un mouse e una tastiera. Esempi di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> viste sono la visualizzazione di testo dell'editor e la finestra di **output** .

  Nell'esempio seguente vengono illustrati gli attributi di esportazione nel provider dell'area di strumenti.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Un'area di strumenti di negoziazione dello spazio è una che occupa lo spazio allo stesso livello del testo. Per creare questo tipo di area di strumenti, è necessario definire una classe di tag che erediti da <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> , che definisce la quantità di spazio occupata dall'area di modifica.

 Come per tutte le aree di ornamento, è necessario esportare la definizione del livello di area di strumenti.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Per creare un'istanza dell'area di strumenti di negoziazione dello spazio, è necessario creare una classe che implementi <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , oltre alla classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (come con altri tipi di aree di strumenti).

 Per registrare il provider di tag, è necessario esportarlo insieme ai seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: tipo di contenuto (ad esempio, "testo" o "codice") per cui l'area di lavoro è valida.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: tipo di visualizzazione di testo per cui questo tag o area di visualizzazione è valido. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> dispone del set di ruoli della visualizzazione di testo predefiniti. Ad esempio, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> viene utilizzato principalmente per le visualizzazioni di testo dei file. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> viene usato per le visualizzazioni di testo che un utente può modificare o spostarsi usando un mouse e una tastiera. Esempi di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> viste sono la visualizzazione di testo dell'editor e la finestra di **output** .

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: il tipo di tag o area di ornamento definito. È necessario aggiungere un secondo <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> per <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> .

  Nell'esempio seguente vengono illustrati gli attributi di esportazione nel provider di tag per un tag di area di negoziazione con negoziazione dello spazio.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Estensione di processori mouse
 È possibile aggiungere una gestione speciale per l'input del mouse. Creare una classe che erediti da <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> ed esegua l'override degli eventi del mouse per l'input che si vuole gestire. È inoltre necessario implementare <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> in una seconda classe ed esportarla insieme all'oggetto <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> che specifica il tipo di contenuto (ad esempio, "testo" o "codice") per il quale il gestore del mouse è valido.

 Nell'esempio seguente vengono illustrati gli attributi di esportazione in un provider del processore del mouse.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Estendi gestori di rilascio
 È possibile personalizzare il comportamento dei gestori di rilascio per tipi specifici di testo creando una classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> e una seconda classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> per creare il gestore di trascinamento. È necessario esportare il gestore di trascinamento insieme ai seguenti attributi:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: il formato di testo per il quale questo gestore di trascinamento è valido. I formati seguenti vengono gestiti in ordine di priorità dal più alto al più basso:

  1. Qualsiasi formato personalizzato

  2. FileDrop

  3. EnhancedMetafile

  4. WaveAudio

  5. Riff

  6. DIF

  7. Impostazioni locali

  8. Tavolozza

  9. PenData

  10. Serializable

  11. SymbolicLink

  12. XAML

  13. XamlPackage

  14. Tiff

  15. Bitmap

  16. DIB

  17. MetafilePicture

  18. CSV

  19. System.String

  20. Formato HTML

  21. UnicodeText

  22. OEMText

  23. Testo

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome del gestore di trascinamento.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: ordinamento del gestore di trascinamento prima o dopo il gestore di rilascio predefinito. Il gestore di rilascio predefinito per Visual Studio è denominato "DefaultFileDropHandler".

  Nell'esempio seguente vengono illustrati gli attributi di esportazione in un provider del gestore di rilascio.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Estensione delle opzioni dell'editor
 È possibile definire le opzioni in modo che siano valide solo in un determinato ambito, ad esempio in una visualizzazione di testo. L'editor fornisce questo set di opzioni predefinite: opzioni dell'editor, opzioni di visualizzazione e opzioni di visualizzazione Windows Presentation Foundation (WPF). Queste opzioni sono disponibili in <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> , <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> e <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> .

 Per aggiungere una nuova opzione, derivare una classe da una delle classi di definizioni di opzioni seguenti:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  Nell'esempio seguente viene illustrato come esportare una definizione di opzione con un valore booleano.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Estendi IntelliSense
 IntelliSense è un termine generale per un gruppo di funzionalità che forniscono informazioni sul testo strutturato e sul completamento delle istruzioni. Queste funzionalità includono il completamento delle istruzioni, la guida per le firme, le informazioni rapide e le lampadine. Il completamento delle istruzioni consente agli utenti di digitare correttamente una parola chiave del linguaggio o un nome di membro. Firma consente di visualizzare la firma o le firme per il metodo che l'utente ha appena digitato. Informazioni rapide Visualizza una firma completa per un nome di tipo o di membro quando il mouse viene posizionato su di esso. La lampadina fornisce azioni aggiuntive per determinati identificatori in determinati contesti, ad esempio la ridenominazione di tutte le occorrenze di una variabile dopo che un'occorrenza è stata rinominata.

 La progettazione di una funzionalità di IntelliSense è molto simile in tutti i casi:

- Un *broker* IntelliSense è responsabile del processo generale.

- Una *sessione* IntelliSense rappresenta la sequenza di eventi tra l'attivazione del Presenter e il commit o l'annullamento della selezione. La sessione viene in genere attivata da un movimento dell'utente.

- Un *controller* IntelliSense è responsabile di decidere quando avviare e terminare la sessione. Stabilisce inoltre quando è necessario eseguire il commit delle informazioni e quando la sessione deve essere annullata.

- Un' *origine* IntelliSense fornisce il contenuto e decide la migliore corrispondenza.

- Un *presentatore* IntelliSense è responsabile della visualizzazione del contenuto.

  Nella maggior parte dei casi, è consigliabile fornire almeno un'origine e un controller. È anche possibile fornire un presentatore se si vuole personalizzare la visualizzazione.

### <a name="implement-an-intellisense-source"></a>Implementare un'origine IntelliSense
 Per personalizzare un'origine, è necessario implementare una o più delle interfacce di origine seguenti:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> è stato deprecato a favore di <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

 Inoltre, è necessario implementare un provider dello stesso tipo:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> è stato deprecato a favore di <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> .

 È necessario esportare il provider insieme ai seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome dell'origine.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: tipo di contenuto (ad esempio, "testo" o "codice") a cui si applica l'origine.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: ordine di visualizzazione dell'origine (rispetto ad altre origini).

- Nell'esempio seguente vengono illustrati gli attributi di esportazione in un provider di origine di completamento.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Per ulteriori informazioni sull'implementazione di origini IntelliSense, vedere le procedure dettagliate seguenti:

- [Procedura dettagliata: visualizzare le descrizioni comandi di informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Procedura dettagliata: visualizzare la guida per la firma](../extensibility/walkthrough-displaying-signature-help.md)

- [Procedura dettagliata: Visualizzare il completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implementare un controller IntelliSense
 Per personalizzare un controller, è necessario implementare l' <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interfaccia. Inoltre, è necessario implementare un provider del controller insieme ai seguenti attributi:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome del controller.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: tipo di contenuto (ad esempio, "testo" o "codice") a cui si applica il controller.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: ordine in cui deve essere visualizzato il controller (rispetto ad altri controller).

  Nell'esempio seguente vengono illustrati gli attributi di esportazione in un provider del controller di completamento.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Per ulteriori informazioni sull'utilizzo dei controller IntelliSense, vedere le procedure dettagliate seguenti:

- [Procedura dettagliata: visualizzare le descrizioni comandi di informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
