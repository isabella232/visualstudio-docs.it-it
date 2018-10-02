---
title: Servizio di linguaggio e punti di estensione dell'Editor | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: 34
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 617af81f4845eb8557db4c134101091eb0b5ae8d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518725"
---
# <a name="language-service-and-editor-extension-points"></a>Punti di estensione dei servizi di linguaggio e dell'editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [servizio di linguaggio e punti di estensione Editor](https://docs.microsoft.com/visualstudio/extensibility/language-service-and-editor-extension-points).  
  
L'editor fornisce punti di estensione che è possibile estendere come parti componente Managed Extensibility Framework (MEF), tra cui la maggior parte delle funzionalità del servizio linguaggio. Ecco le categorie di punto di estensione principale:  
  
-   Tipi di contenuto  
  
-   Tipi di classificazione e formati di classificazione  
  
-   Le barre di scorrimento e i margini  
  
-   Tag  
  
-   Aree di controllo  
  
-   Processori del mouse  
  
-   Gestori di rilascio  
  
-   Opzioni  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>Estensione di tipi di contenuto  
 I tipi di contenuto sono le definizioni dei tipi di testo gestite dall'editor, ad esempio, "text", "code" o "CSharp". Definire un nuovo tipo di contenuto dichiarando una variabile del tipo <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> e fornendo il nuovo tipo di contenuto di un nome univoco. Per registrare il tipo di contenuto con l'editor, esportarlo con gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute> è il nome del tipo di contenuto.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> è il nome del tipo di contenuto da cui deriva questo tipo di contenuto. Un tipo di contenuto può ereditare da più altri tipi di contenuto.  
  
 Poiché il <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> classe è sealed, è possibile esportarlo con nessun parametro di tipo.  
  
 Nell'esempio seguente illustra gli attributi di esportazione su una definizione di tipo di contenuto.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 I tipi di contenuto possono essere basati su zero o più tipi di contenuto pre-esistenti. Questi sono i tipi predefiniti:  
  
-   Qualsiasi: il tipo di contenuto base. Elemento padre di tutti gli altri tipi di contenuto.  
  
-   Text: il tipo di base per il contenuto non proiezione. Eredita da "any".  
  
-   Testo normale: per il testo non di codice. Eredita da "text".  
  
-   Codice: per il codice di tutti i tipi. Eredita da "text".  
  
-   Inerte: esclude il testo da tutti i tipi di gestione. Testo di questo tipo di contenuto non avrà mai qualsiasi estensione applicata ad esso.  
  
-   Proiezione: per il contenuto del buffer di proiezione. Eredita da "any".  
  
-   IntelliSense: per il contenuto di IntelliSense. Eredita da "text".  
  
-   Sighelp: supporto per la firma. Eredita da "intellisense".  
  
-   Sighelp-doc: documentazione della Guida firma. Eredita da "intellisense".  
  
 Questi sono alcuni dei tipi di contenuto che sono definiti da Visual Studio e alcuni dei linguaggi che sono ospitati in Visual Studio:  
  
-   Basic  
  
-   C/C++  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   Risultati ricerca  
  
-   F#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 Per individuare l'elenco dei tipi di contenuto disponibili, importare il <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, che gestisce la raccolta di tipi di contenuto per l'editor. Il codice seguente importa questo servizio come proprietà.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Per associare un tipo di contenuto con un'estensione di file, usare <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  In Visual Studio, estensioni di file registrate mediante il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> a un pacchetto del servizio di linguaggio. Il <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> associa un tipo di contenuto MEF con un'estensione che è stata registrata in questo modo.  
  
 Per esportare l'estensione alla definizione del tipo di contenuto, è necessario includere gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: specifica l'estensione del nome file.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Specifica il tipo di contenuto.  
  
 Poiché il <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> classe è sealed, è possibile esportarlo con nessun parametro di tipo.  
  
 Nell'esempio seguente illustra gli attributi di esportazione in un'estensione a una definizione di tipo di contenuto.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 Il <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> gestisce le associazioni tra estensioni di file e i tipi di contenuto.  
  
## <a name="extending-classification-types-and-classification-formats"></a>Formati di estensione di classificazione e i tipi di classificazione  
 È possibile utilizzare i tipi di classificazione per definire i tipi di testo per il quale si desidera fornire una gestione differente (ad esempio, la colorazione del testo "parola chiave" blu e il testo "comment" verde). Definire un nuovo tipo di classificazione dichiarando una variabile di tipo <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> e assegnargli un nome univoco.  
  
 Per registrare il tipo di classificazione con l'editor, esportarlo con gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del tipo di classificazione.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: il nome del tipo di classificazione da cui eredita questo tipo di classificazione. Tutti i tipi di classificazione ereditano da "text", e un tipo di classificazione da diversi altri tipi di classificazione.  
  
 Poiché il <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> classe è sealed, è possibile esportarlo con nessun parametro di tipo.  
  
 Nell'esempio seguente illustra gli attributi di esportazione su una definizione del tipo di classificazione.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 Il <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> fornisce l'accesso alle classificazioni standard. Questi tipi di classificazione predefinite:  
  
-   "text"  
  
-   "linguaggio naturale" (deriva da "text")  
  
-   "linguaggio formale" (deriva da "text")  
  
-   "string" (deriva dal valore "literal")  
  
-   "character" (deriva dal valore "literal")  
  
-   "numerici" (deriva dal valore "literal")  
  
 Un set di diversi tipi di errore ereditano da <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Includono i tipi di errore seguente:  
  
-   "errore di sintassi"  
  
-   "Errore del compilatore"  
  
-   "altro errore"  
  
-   "avviso"  
  
 Per individuare l'elenco dei tipi di classificazione disponibili, importare il <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, che gestisce la raccolta di tipi di classificazione per l'editor. Il codice seguente importa questo servizio come proprietà.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 È possibile definire una definizione di formato di classificazione per il nuovo tipo di classificazione. Derivare una classe dalla classe <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> ed esportarlo con il tipo <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>, insieme con gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del formato.  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: il nome visualizzato del formato.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Specifica se il formato viene visualizzato nei **i tipi di carattere e colori** pagina della **opzioni** nella finestra di dialogo.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: la priorità del formato. Valori validi sono compresi tra <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: digitare il nome della classificazione di cui eseguire il mapping in questo formato.  
  
 Nell'esempio seguente illustra gli attributi di esportazione su una definizione di formato di classificazione.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Per individuare l'elenco dei formati disponibili, importare il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, che gestisce la raccolta di formati per l'editor. Il codice seguente importa questo servizio come proprietà.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extending-margins-and-scrollbars"></a>Le barre di scorrimento e dell'estensione  
 Le barre di scorrimento e i margini sono gli elementi di visualizzazione principale dell'editor oltre alla visualizzazione di testo stesso. È possibile fornire un numero qualsiasi di margini oltre i margini standard visualizzati intorno alla visualizzazione di testo.  
  
 Implementare un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interfaccia per definire un margine. È inoltre necessario implementare il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfaccia per creare il margine.  
  
 Per registrare il provider di margine con l'editor, è necessario esportare il provider con gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del margine.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordine in cui viene visualizzato il margine, rispetto a dei margini.  
  
     Questi sono i margini predefiniti:  
  
    -   "Barra di scorrimento orizzontale Wpf"  
  
    -   "Barra di scorrimento verticale Wpf"  
  
    -   "Margine del numero di riga Wpf"  
  
     I margini orizzontali che hanno un attributo di ordine di `After="Wpf Horizontal Scrollbar"` sono visualizzate sotto il margine predefinito e i margini orizzontali che hanno un attributo di ordine di `Before ="Wpf Horizontal Scrollbar"` vengono visualizzati sopra il margine predefinito. Pulsante destro del mouse margini verticali che hanno un attributo di ordine di `After="Wpf Vertical Scrollbar"` vengono visualizzati a destra della barra di scorrimento. A sinistra dei margini verticali che hanno un attributo di ordine di `After="Wpf Line Number Margin"` vengono visualizzate a sinistra del margine del numero di riga (se è visibile).  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: il tipo del margine di (a sinistra, destra, superiore o inferiore).  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "text" o "code") per il quale il margine è valido.  
  
 Nell'esempio seguente illustra gli attributi di esportazione in un provider di margine per il margine visualizzato a destra del margine del numero di riga.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>Estendere i tag  
 I tag sono un modo per associare dati a diversi tipi di testo. In molti casi, i dati associati vengono visualizzati come un effetto visivo, ma non tutti i tag sono una rappresentazione visiva. È possibile definire il proprio tipo di tag implementando <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. È inoltre necessario implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> per fornire i tag per un determinato set di intervalli di testo e un <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> per fornire il tagger. È necessario esportare il provider di tagger insieme gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "text" o "code") per il quale il tag è valido.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: il tipo di tag.  
  
 Nell'esempio seguente illustra gli attributi di esportazione in un provider di tagger.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TagType(typeof(TestTag))]  
internal class TestTaggerProvider : ITaggerProvider  
```  
  
 I tipi di tag seguenti sono incorporati:  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: associato un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: associati ai tipi di errore.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: associata a un'area di controllo.  
  
    > [!NOTE]
    >  Per un esempio di un <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, vedere la definizione HighlightWordTag [questa procedura dettagliata: evidenziazione testo](../extensibility/walkthrough-highlighting-text.md).  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: associati con aree che possono essere espansi o compressi nella struttura.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definisce lo spazio che occupa un'area di controllo in una visualizzazione di testo. Per altre informazioni sulle aree di controllo di negoziazione spazio, vedere la sezione seguente.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: fornisce il ridimensionamento per l'area di controllo e spaziatura automatica.  
  
 Per trovare e usare i tag per i buffer e le viste, importare il <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> o il <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, che offrono un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> del tipo richiesto. Il codice seguente importa questo servizio come proprietà.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>I tag e MarkerFormatDefinitions  
 È possibile estendere il <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> classe per definire l'aspetto di un tag. È necessario esportare la classe (come un <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) con gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nome utilizzato per fare riferimento a questo formato  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: in questo modo, il formato da visualizzare nell'interfaccia utente  
  
 Nel costruttore, si definiscono il nome visualizzato e l'aspetto del tag. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> definisce il colore di riempimento e <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> definisce il colore del bordo. Il <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> è il nome della definizione del formato localizzabile.  
  
 Di seguito è riportato un esempio di una definizione di formato:  
  
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
  
 Per applicare la definizione del formato di un tag, fare riferimento al nome che è impostato nell'attributo nome della classe (non il nome visualizzato).  
  
> [!NOTE]
>  Per un esempio di un <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, vedere la classe HighlightWordFormatDefinition nello [questa procedura dettagliata: evidenziazione testo](../extensibility/walkthrough-highlighting-text.md).  
  
## <a name="extending-adornments"></a>Estensione di aree di controllo  
 Le aree di controllo definiscono gli effetti visivi che possono essere aggiunti al testo che viene visualizzato in una visualizzazione di testo o al testo della visualizzazione stessa. È possibile definire la propria area di controllo come qualsiasi tipo di <xref:System.Windows.UIElement>.  
  
 Nella classe dell'area di controllo, è necessario dichiarare un <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Per registrare il livello di area di controllo, esportarlo con gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome dell'area di controllo.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordinamento dell'area di controllo per quanto riguarda gli altri livelli dell'area di controllo. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> definisce quattro livelli predefinito: selezione, struttura, punto di inserimento e testo.  
  
 Nell'esempio seguente illustra gli attributi di esportazione su una definizione del livello di area di controllo.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 È necessario creare una seconda classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> e gestisce il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> eventi creando un'area di controllo. È necessario esportare questa classe insieme gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "text" o "code") per il quale l'area di controllo è valido.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: il tipo di visualizzazione di testo per il quale questa area di controllo è valido. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> include il set di ruoli della visualizzazione di testo predefiniti. Ad esempio, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> viene usata principalmente per le visualizzazioni di testo dei file. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> viene usato per le visualizzazioni di testo che un utente può modificare o passare tramite mouse e tastiera. Esempi di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> le visualizzazioni sono la visualizzazione dell'editor di testo e il **Output** finestra.  
  
 Nell'esempio seguente illustra gli attributi di esportazione per il provider dell'area di controllo.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Un'area di controllo di negoziazione spazio è quello che occupa spazio allo stesso livello del testo. Per creare questo tipo di area di controllo, è necessario definire una classe di tag che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, che definisce la quantità di spazio che occupa l'area di controllo.  
  
 Come con tutte le aree di controllo, è necessario esportare la definizione del livello di area di controllo.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Per creare un'istanza dell'area di controllo di negoziazione spazio, è necessario creare una classe che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, oltre alla classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (come con altri tipi di aree di controllo).  
  
 Per registrare il provider di tagger, è necessario esportarlo insieme gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "text" o "code") per il quale l'area di controllo è valido.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: il tipo di visualizzazione di testo per il quale l'area di controllo o il tag è valido. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> include il set di ruoli della visualizzazione di testo predefiniti. Ad esempio, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> viene usata principalmente per le visualizzazioni di testo dei file. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> viene usato per le visualizzazioni di testo che un utente può modificare o passare tramite mouse e tastiera. Esempi di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> le visualizzazioni sono la visualizzazione dell'editor di testo e il **Output** finestra.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: tipo di tag o area di controllo che sono state definite. È necessario aggiungere una seconda <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> per <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
 Nell'esempio seguente illustra gli attributi di esportazione nel provider di tagger per un tag di area di controllo di negoziazione spazio.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>Estensione di processori del Mouse  
 È possibile aggiungere una gestione speciale per l'input del mouse. Creare una classe che eredita da <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> ed eseguire l'override gli eventi del mouse per l'input che si desidera gestire. È inoltre necessario implementare <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> in una seconda classe ed esportarlo con la <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> che specifica il tipo di contenuto (ad esempio, "text" o "code") per il quale il gestore del mouse è valido.  
  
 Nell'esempio seguente illustra gli attributi di esportazione in un provider di processore del mouse.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>Estensione di gestori di rilascio  
 È possibile personalizzare il comportamento dei gestori di rilascio per tipi specifici di testo mediante la creazione di una classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> e una seconda classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> per creare il gestore del trascinamento. È necessario esportare il gestore del trascinamento insieme gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: il formato di testo per il quale il gestore del trascinamento è valido. I formati seguenti vengono gestiti in ordine di priorità dal valore più alto al più basso:  
  
    1.  Formati personalizzati  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  WaveAudio  
  
    5.  RIFF  
  
    6.  DIF  
  
    7.  Impostazioni locali  
  
    8.  Tavolozza  
  
    9. PenData  
  
    10. Serializzabile  
  
    11. SymbolicLink  
  
    12. XAML  
  
    13. XamlPackage  
  
    14. TIFF  
  
    15. Bitmap  
  
    16. DIB  
  
    17. MetafilePicture  
  
    18. CSV  
  
    19. System.String  
  
    20. Formato HTML  
  
    21. UnicodeText  
  
    22. OEMText  
  
    23. Testo  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del gestore di trascinamento.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordinamento del gestore di trascinamento prima o dopo il gestore del trascinamento predefinito. Il gestore del trascinamento predefinito per Visual Studio è denominato "DefaultFileDropHandler".  
  
 Nell'esempio seguente illustra gli attributi di esportazione in un provider di gestore di trascinamento.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>Estensione di opzioni dell'Editor  
 È possibile definire le opzioni per essere valido solo in un determinato ambito, ad esempio, in una visualizzazione di testo. L'editor fornisce questo set di opzioni predefinite: le opzioni dell'editor, visualizzare le opzioni e le opzioni di visualizzazione di Windows Presentation Foundation (WPF). Queste opzioni sono reperibile nel <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, e <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Per aggiungere una nuova opzione, derivare una classe da una di queste classi di definizione di opzione:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 Nell'esempio seguente viene illustrato come esportare una definizione di opzione con un valore booleano.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>Estensione di IntelliSense  
 IntelliSense è un termine generale per un gruppo di funzionalità che forniscono informazioni sul testo strutturato e il completamento delle istruzioni per tale. Queste funzionalità includono il completamento delle istruzioni, supporto per la firma, le informazioni rapide e lampadine. Completamento istruzioni consente agli utenti di digitare un nome di linguaggio parola chiave o un membro in modo corretto. Supporto per la firma Visualizza la firma o le firme del metodo che ha appena digitato dall'utente. Informazioni rapide visualizza una firma completa per un nome di tipo o membro quando si sofferma il mouse su di esso. Lampadina fornire azioni aggiuntive per alcuni identificatori in determinati contesti, ad esempio, la ridenominazione di tutte le occorrenze di una variabile dopo la ridenominazione di un'occorrenza.  
  
 La progettazione di una funzionalità IntelliSense è molto simile in tutti i casi:  
  
-   Un IntelliSense *broker* è responsabile per il processo complessivo.  
  
-   Un IntelliSense *sessione* rappresenta la sequenza di eventi tra l'attivazione del presentatore e la fase di commit o l'annullamento della selezione. La sessione viene in genere attivata da un movimento dell'utente.  
  
-   Un IntelliSense *controller* è responsabile per decidere quando la sessione deve iniziare e terminare. Decide anche quando le informazioni devono essere eseguito il commit e quando la sessione deve essere annullata.  
  
-   Un IntelliSense *origine* fornisce il contenuto e determina la migliore corrispondenza.  
  
-   Un IntelliSense *presenter* è responsabile della visualizzazione del contenuto.  
  
 Nella maggior parte dei casi, è consigliabile specificare almeno un'origine e un controller. È anche possibile fornire un presentatore se si desidera personalizzare la visualizzazione.  
  
### <a name="implementing-an-intellisense-source"></a>Implementazione di un'origine di IntelliSense  
 Per personalizzare un'origine, è necessario implementare uno (o più) delle interfacce di origine seguenti:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> è stato deprecato in favore di <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 Inoltre, è necessario implementare un provider dello stesso tipo:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> è stato deprecato in favore di <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 È necessario esportare il provider con gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome dell'origine.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "text" o "code") a cui si applica l'origine.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordine in cui l'origine deve essere visualizzato (in relazione ad altre origini).  
  
-   Nell'esempio seguente illustra gli attributi di esportazione in un provider di origine di completamento.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Per altre informazioni sull'implementazione di origini di IntelliSense, vedere le procedure dettagliate seguenti:  
  
 [Procedura dettagliata: Visualizzazione delle informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Procedura dettagliata: Visualizzazione della funzionalità di supporto alla firma](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Procedura dettagliata: Visualizzazione del completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>Implementazione di un Controller IntelliSense  
 Per personalizzare un controller, è necessario implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interfaccia. Inoltre, è necessario implementare un provider di controller insieme gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del controller.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "text" o "code") a cui si applica al controller.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordine in cui il controller deve essere visualizzato (in relazione gli altri controller).  
  
 Nell'esempio seguente illustra gli attributi di esportazione in un provider di controller di completamento.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Per altre informazioni sull'uso di controller IntelliSense, vedere le procedure dettagliate seguenti:  
  
 [Procedura dettagliata: Visualizzazione delle informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

