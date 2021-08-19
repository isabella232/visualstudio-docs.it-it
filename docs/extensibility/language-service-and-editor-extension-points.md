---
title: Punti di estensione del servizio di linguaggio e dell'editor | Microsoft Docs
description: Informazioni sui punti di estensione nell'editor Visual Studio codice che è possibile estendere, incluse la maggior parte delle funzionalità del servizio di linguaggio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c3a97b75f1df66d8353c06acf74f8d69b26a6e8c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152250"
---
# <a name="language-service-and-editor-extension-points"></a>Punti di estensione del servizio di linguaggio e dell'editor
L'editor fornisce punti di estensione che è possibile estendere come Managed Extensibility Framework (MEF), incluse la maggior parte delle funzionalità del servizio di linguaggio. Queste sono le categorie principali dei punti di estensione:

- Tipi di contenuto

- Tipi di classificazione e formati di classificazione

- Margini e barre di scorrimento

- Tag

- Ornamenti

- Processori del mouse

- Gestori di eliminazione

- Opzioni

- IntelliSense

## <a name="extend-content-types"></a>Estendere i tipi di contenuto
 I tipi di contenuto sono definizioni dei tipi di testo gestiti dall'editor, ad esempio "text", "code" o "CSharp". Per definire un nuovo tipo di contenuto, dichiarare una variabile del tipo e assegnare al nuovo tipo <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> di contenuto un nome univoco. Per registrare il tipo di contenuto con l'editor, esportarlo con gli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> è il nome del tipo di contenuto.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> è il nome del tipo di contenuto da cui deriva questo tipo di contenuto. Un tipo di contenuto può ereditare da più altri tipi di contenuto.

  Poiché la <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> classe è sealed, è possibile esportarla senza parametri di tipo.

  L'esempio seguente illustra gli attributi di esportazione in una definizione di tipo di contenuto.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 I tipi di contenuto possono essere basati su zero o più tipi di contenuto preesiste. Questi sono i tipi predefiniti:

- Qualsiasi: il tipo di contenuto di base. Padre di tutti gli altri tipi di contenuto.

- Text: tipo di base per il contenuto non di proiezione. Eredita da "any".

- Testo non crittografato: per testo non in codice. Eredita da "text".

- Codice: per codice di tutti i tipi. Eredita da "text".

- Inert: esclude il testo da qualsiasi tipo di gestione. Al testo di questo tipo di contenuto non verrà mai applicata alcuna estensione.

- Proiezione: per il contenuto dei buffer di proiezione. Eredita da "any".

- Intellisense: per il contenuto di IntelliSense. Eredita da "text".

- Sighelp: guida alla firma. Eredita da "intellisense".

- Sighelp-doc: documentazione della Guida per la firma. Eredita da "intellisense".

  Di seguito sono riportati alcuni tipi di contenuto definiti da Visual Studio e alcuni dei linguaggi ospitati in Visual Studio:

- Basic

- C/C++

- ConsoleOutput

- CSharp

- CSS

- Enc

- FindResults

- F#

- HTML

- JScript

- XAML

- XML

  Per individuare l'elenco dei tipi di contenuto disponibili, importare , che <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> gestisce la raccolta di tipi di contenuto per l'editor. Il codice seguente importa questo servizio come proprietà.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Per associare un tipo di contenuto a un'estensione di file, usare <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> .

> [!NOTE]
> In Visual Studio, le estensioni di file vengono registrate usando in <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> un pacchetto del servizio di linguaggio. Associa <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> un tipo di contenuto MEF a un'estensione di file registrata in questo modo.

 Per esportare l'estensione del nome file nella definizione del tipo di contenuto, è necessario includere gli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: specifica l'estensione di file.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: specifica il tipo di contenuto.

  Poiché la <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> classe è sealed, è possibile esportarla senza parametri di tipo.

  L'esempio seguente illustra gli attributi di esportazione di un'estensione di file in una definizione di tipo di contenuto.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 gestisce <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> le associazioni tra estensioni di file e tipi di contenuto.

## <a name="extend-classification-types-and-classification-formats"></a>Estendere i tipi di classificazione e i formati di classificazione
 È possibile usare i tipi di classificazione per definire i tipi di testo per cui si vuole fornire una gestione diversa, ad esempio colorando il testo "parola chiave" blu e il testo "commento" in verde. Definire un nuovo tipo di classificazione dichiarando una variabile di tipo <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> e assegnargli un nome univoco.

 Per registrare il tipo di classificazione con l'editor, esportarlo con gli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome del tipo di classificazione.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: nome del tipo di classificazione da cui eredita questo tipo di classificazione. Tutti i tipi di classificazione ereditano da "text" e un tipo di classificazione può ereditare da più altri tipi di classificazione.

  Poiché la <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> classe è sealed, è possibile esportarla senza parametri di tipo.

  L'esempio seguente illustra gli attributi di esportazione in una definizione del tipo di classificazione.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 fornisce <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> l'accesso alle classificazioni standard. I tipi di classificazione predefiniti includono:

- "text"

- "linguaggio naturale" (deriva da "text")

- "linguaggio formale" (deriva da "text")

- "string" (deriva da "literal")

- "character" (deriva da "literal")

- "numerical" (deriva da "literal")

  Un set di tipi di errore diversi eredita da <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> . Includono i tipi di errore seguenti:

- "Errore di sintassi"

- "Errore del compilatore"

- "altro errore"

- "avviso"

  Per individuare l'elenco dei tipi di classificazione disponibili, importare <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> , che gestisce la raccolta di tipi di classificazione per l'editor. Il codice seguente importa questo servizio come proprietà.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 È possibile definire una definizione del formato di classificazione per il nuovo tipo di classificazione. Derivare una classe <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> da ed esportarla con il tipo <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> , insieme agli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome del formato.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: nome visualizzato del formato.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: specifica se il formato viene visualizzato nella pagina Tipi di carattere **e** colori della **finestra di dialogo** Opzioni .

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: priorità del formato. I valori validi sono di <xref:Microsoft.VisualStudio.Text.Classification.Priority> .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: nome del tipo di classificazione a cui viene eseguito il mapping di questo formato.

  L'esempio seguente illustra gli attributi di esportazione in una definizione di formato di classificazione.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Per individuare l'elenco dei formati disponibili, importare <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> , che gestisce la raccolta di formati per l'editor. Il codice seguente importa questo servizio come proprietà.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Estendere margini e barre di scorrimento
 Margini e barre di scorrimento sono gli elementi principali della visualizzazione dell'editor oltre alla visualizzazione testo stessa. Oltre ai margini standard visualizzati intorno alla visualizzazione testo, è possibile specificare un numero qualsiasi di margini.

 Implementare <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> un'interfaccia per definire un margine. È inoltre necessario implementare <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> l'interfaccia per creare il margine.

 Per registrare il provider margin con l'editor, è necessario esportare il provider insieme agli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome del margine.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordine in cui viene visualizzato il margine rispetto agli altri margini.

   I margini predefiniti sono i seguenti:

  - "Barra di scorrimento orizzontale wpf"

  - "Barra di scorrimento verticale Wpf"

  - "Margine numero di riga Wpf"

    I margini orizzontali con un attributo order di vengono visualizzati sotto il margine incorporato e i margini orizzontali con un attributo order di vengono visualizzati sopra il `After="Wpf Horizontal Scrollbar"` `Before ="Wpf Horizontal Scrollbar"` margine incorporato. I margini verticali a destra con un attributo order di `After="Wpf Vertical Scrollbar"` vengono visualizzati a destra della barra di scorrimento. I margini verticali a sinistra con un attributo order di vengono visualizzati a sinistra del margine del numero di riga `After="Wpf Line Number Margin"` (se visibile).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: tipo di margine (sinistro, destro, superiore o inferiore).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "text" o "code") per il quale il margine è valido.

  L'esempio seguente illustra gli attributi di esportazione in un provider di margini per un margine visualizzato a destra del margine del numero di riga.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Estendere i tag
 I tag sono un modo per associare i dati a diversi tipi di testo. In molti casi, i dati associati vengono visualizzati come effetto visivo, ma non tutti i tag hanno una presentazione visiva. È possibile definire un tipo di tag personalizzato implementando <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . È inoltre necessario <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementare per fornire i tag per un determinato set di intervalli di testo e per <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> fornire il tagger. È necessario esportare il provider di tagger insieme agli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: tipo di contenuto (ad esempio, "text" o "code") per il quale il tag è valido.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: tipo di tag.

  L'esempio seguente illustra gli attributi di esportazione in un provider di tagger.

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> I tipi di tag seguenti sono predefiniti:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: associato a un oggetto <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: associato ai tipi di errore.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: associato a un'area di controllo.

  > [!NOTE]
  > Per un esempio di <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> , vedere la definizione HighlightWordTag in Procedura [dettagliata: Evidenziazione del testo.](../extensibility/walkthrough-highlighting-text.md)

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: associato ad aree che possono essere espanse o compresse nella struttura.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definisce lo spazio che un'area di controllo occupa in una visualizzazione testo. Per altre informazioni sulle aree di controllo per la negoziazione dello spazio, vedere la sezione seguente.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: fornisce spaziatura e ridimensionamento automatici per l'area di controllo.

  Per trovare e usare tag per buffer e visualizzazioni, importare o , che forniscono <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> un oggetto del tipo <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> richiesto. Il codice seguente importa questo servizio come proprietà.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Tag e MarkerFormatDefinitions
 È possibile estendere la <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> classe per definire l'aspetto di un tag. È necessario esportare la classe (come <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> ) con gli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome usato per fare riferimento a questo formato

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: in questo modo il formato viene visualizzato nell'interfaccia utente

  Nel costruttore si definiscono il nome visualizzato e l'aspetto del tag. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> definisce il colore di riempimento e <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> il colore del bordo. è <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> il nome localizzabile della definizione di formato.

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

 Per applicare questa definizione di formato a un tag, fare riferimento al nome impostato nell'attributo name della classe (non al nome visualizzato).

> [!NOTE]
> Per un esempio di <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> , vedere la classe HighlightWordFormatDefinition in Procedura [dettagliata: Evidenziazione del testo.](../extensibility/walkthrough-highlighting-text.md)

## <a name="extend-adornments"></a>Estendere le aree di controllo
 Le aree di controllo definiscono gli effetti visivi che possono essere aggiunti al testo visualizzato in una visualizzazione testo o alla visualizzazione testo stessa. È possibile definire un'area di controllo come qualsiasi tipo di <xref:System.Windows.UIElement> .

 Nella classe dell'area di controllo è necessario dichiarare un oggetto <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> . Per registrare il livello di area di controllo, esportarlo con gli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome dell'area di controllo.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: ordinamento dell'area di controllo rispetto ad altri livelli dell'area di controllo. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> definisce quattro livelli predefiniti: Selection, Outlining, Caret e Text.

  L'esempio seguente mostra gli attributi di esportazione in una definizione di livello di area di controllo.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 È necessario creare una seconda classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> e gestisce il relativo evento creando <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> un'istanza dell'area di controllo. È necessario esportare questa classe con gli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: tipo di contenuto (ad esempio, "text" o "code") per il quale l'area di controllo è valida.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: tipo di visualizzazione testo per cui questa area di controllo è valida. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> include il set di ruoli di visualizzazione testo predefiniti. Ad esempio, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> viene usato principalmente per le visualizzazioni di testo dei file. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> viene usato per le visualizzazioni di testo che un utente può modificare o navigare usando un mouse e una tastiera. Esempi di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> visualizzazioni sono la visualizzazione testo dell'editor e la **finestra Output.**

  L'esempio seguente mostra gli attributi di esportazione nel provider dell'area di controllo.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Un'area di controllo che negozia lo spazio occupa spazio allo stesso livello del testo. Per creare questo tipo di area di controllo, è necessario definire una classe di tag che eredita da , che definisce la quantità di spazio occupata <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> dall'area di controllo.

 Come per tutte le aree di controllo, è necessario esportare la definizione del livello dell'area di controllo.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Per creare un'istanza dell'area di controllo per la negoziazione dello spazio, è necessario creare una classe che implementa , oltre alla classe che implementa (come con altri <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> tipi di aree di <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> controllo).

 Per registrare il provider di tagger, è necessario esportarlo insieme agli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: tipo di contenuto (ad esempio, "text" o "code") per il quale l'area di controllo è valida.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: tipo di visualizzazione di testo per cui questo tag o area di controllo è valido. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> include il set di ruoli di visualizzazione testo predefiniti. Ad esempio, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> viene usato principalmente per le visualizzazioni di testo dei file. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> viene usato per le visualizzazioni di testo che un utente può modificare o navigare usando un mouse e una tastiera. Esempi di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> visualizzazioni sono la visualizzazione testo dell'editor e la **finestra Output.**

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: tipo di tag o area di controllo definita. È necessario aggiungere un secondo <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> per <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> .

  L'esempio seguente mostra gli attributi di esportazione nel provider di tag per un tag di area di controllo che negozia lo spazio.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Estensione dei processori del mouse
 È possibile aggiungere una gestione speciale per l'input del mouse. Creare una classe che eredita da ed eseguire <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> l'override degli eventi del mouse per l'input che si desidera gestire. È inoltre necessario implementare in una seconda classe ed esportarlo insieme a che specifica il tipo di contenuto <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> (ad esempio, "text" o "code") per il quale il gestore <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> del mouse è valido.

 Nell'esempio seguente vengono illustrati gli attributi di esportazione in un provider del processore del mouse.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Estendere i gestori di rilascio
 È possibile personalizzare il comportamento dei gestori di rilascio per tipi specifici di testo creando una classe che implementa e una seconda classe che implementa per <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> creare il gestore di <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> rilascio. È necessario esportare il gestore di rilascio con gli attributi seguenti:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: formato di testo per il quale questo gestore di rilascio è valido. I formati seguenti vengono gestiti in ordine di priorità dal più alto al più basso:

  1. Qualsiasi formato personalizzato

  2. Filedrop

  3. EnhancedMetafile

  4. Waveaudio

  5. Riff

  6. Dif

  7. Locale

  8. Tavolozza

  9. PenData

  10. Serializable

  11. SymbolicLink

  12. Xaml

  13. XamlPackage

  14. Tiff

  15. Bitmap

  16. Dib

  17. MetafilePicture

  18. CSV

  19. System.String

  20. Formato HTML

  21. Unicodetext

  22. OEMText

  23. Testo

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome del gestore di rilascio.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: ordinamento del gestore di rilascio prima o dopo il gestore di rilascio predefinito. Il gestore di rilascio predefinito per Visual Studio denominato "DefaultFileDropHandler".

  Nell'esempio seguente vengono illustrati gli attributi di esportazione in un provider del gestore di rilascio.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Estensione delle opzioni dell'editor
 È possibile definire opzioni valide solo in un determinato ambito, ad esempio in una visualizzazione di testo. L'editor fornisce questo set di opzioni predefinite: opzioni dell'editor, opzioni di visualizzazione e Windows Presentation Foundation (WPF). Queste opzioni sono disponibili in <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> , <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> e <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> .

 Per aggiungere una nuova opzione, derivare una classe da una di queste classi di definizione dell'opzione:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  Nell'esempio seguente viene illustrato come esportare una definizione di opzione con un valore booleano.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Estendere IntelliSense
 IntelliSense è un termine generale per un gruppo di funzionalità che forniscono informazioni sul testo strutturato e sul completamento delle istruzioni. Queste funzionalità includono il completamento delle istruzioni, la Guida per la firma, le informazioni rapide e le lampadine. Il completamento delle istruzioni consente agli utenti di digitare correttamente una parola chiave del linguaggio o un nome di membro. La Guida alla firma visualizza la firma o le firme per il metodo appena digitato dall'utente. Informazioni rapide visualizza una firma completa per un nome di tipo o membro quando si posiziona il mouse su di esso. La lampadina fornisce azioni aggiuntive per determinati identificatori in determinati contesti, ad esempio rinominando tutte le occorrenze di una variabile dopo la ridenominazione di un'occorrenza.

 La progettazione di una funzionalità IntelliSense è molto uguale in tutti i casi:

- Un broker IntelliSense  è responsabile del processo complessivo.

- Una sessione IntelliSense  rappresenta la sequenza di eventi tra l'attivazione del presentatore e il commit o l'annullamento della selezione. La sessione viene in genere attivata da un movimento dell'utente.

- Un *controller* IntelliSense è responsabile di decidere quando avviare e terminare la sessione. Decide anche quando eseguire il commit delle informazioni e quando deve essere annullata la sessione.

- Un'origine IntelliSense  fornisce il contenuto e decide la corrispondenza migliore.

- Un presentatore  IntelliSense è responsabile della visualizzazione del contenuto.

  Nella maggior parte dei casi, è consigliabile fornire almeno un'origine e un controller. È anche possibile fornire un presentatore se si vuole personalizzare la visualizzazione.

### <a name="implement-an-intellisense-source"></a>Implementare un'origine IntelliSense
 Per personalizzare un'origine, è necessario implementare una o più delle interfacce di origine seguenti:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> è stato deprecato a favore di <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

 È inoltre necessario implementare un provider dello stesso tipo:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> è stato deprecato a favore di <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> .

 È necessario esportare il provider con gli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome dell'origine.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: tipo di contenuto (ad esempio, "text" o "code") a cui si applica l'origine.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordine in cui deve essere visualizzata l'origine (rispetto ad altre origini).

- L'esempio seguente illustra gli attributi di esportazione in un provider di origine di completamento.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Per altre informazioni sull'implementazione di origini IntelliSense, vedere le procedure dettagliate seguenti:

- [Procedura dettagliata: Visualizzare le descrizioni comando di Informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Procedura dettagliata: Visualizzare la Guida per la firma](../extensibility/walkthrough-displaying-signature-help.md)

- [Procedura dettagliata: Visualizzare il completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implementare un controller IntelliSense
 Per personalizzare un controller, è necessario implementare <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> l'interfaccia . È inoltre necessario implementare un provider di controller con gli attributi seguenti:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome del controller.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: tipo di contenuto (ad esempio, "text" o "code") a cui si applica il controller.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordine in cui deve essere visualizzato il controller (rispetto ad altri controller).

  L'esempio seguente illustra gli attributi di esportazione in un provider del controller di completamento.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Per altre informazioni sull'uso dei controller IntelliSense, vedere le procedure dettagliate seguenti:

- [Procedura dettagliata: Visualizzare le descrizioni comando di Informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
