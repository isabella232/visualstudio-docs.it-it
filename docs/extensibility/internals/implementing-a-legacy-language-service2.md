---
title: Implementazione di un linguaggio legacy Service2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df44b92cdf311689397a062b127d4c3e514a15e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238699"
---
# <a name="implementing-a-legacy-language-service-2"></a>Implementazione di un servizio di linguaggio Legacy 2
Per implementare un servizio di linguaggio utilizzando il Framework di pacchetto gestito (MPF), è necessario derivare una classe dalla <xref:Microsoft.VisualStudio.Package.LanguageService> classe e implementare i metodi e le proprietà astratti seguenti:

- Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- Proprietà <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Vedere le sezioni appropriate di seguito per informazioni dettagliate sull'implementazione di questi metodi e proprietà.

  Per supportare funzionalità aggiuntive, il servizio di linguaggio potrebbe dover derivare una classe da una delle classi del servizio di linguaggio MPF; per supportare altri comandi di menu, ad esempio, è necessario derivare una classe dalla <xref:Microsoft.VisualStudio.Package.ViewFilter> classe ed eseguire l'override di diversi metodi di gestione dei comandi <xref:Microsoft.VisualStudio.Package.ViewFilter> . per informazioni dettagliate, vedere. La <xref:Microsoft.VisualStudio.Package.LanguageService> classe fornisce diversi metodi chiamati per creare nuove istanze di varie classi ed è necessario eseguire l'override del metodo di creazione appropriato per fornire un'istanza della classe. Ad esempio, è necessario eseguire l'override del <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe per restituire un'istanza della classe personalizzata <xref:Microsoft.VisualStudio.Package.ViewFilter> . Per ulteriori informazioni, vedere la sezione relativa alla creazione di un'istanza delle classi personalizzate.

  Il servizio di linguaggio può anche fornire le proprie icone, che vengono usate in molte posizioni. Ad esempio, quando viene visualizzato un elenco di completamento IntelliSense, a ogni elemento dell'elenco può essere associata un'icona, che contrassegna l'elemento come metodo, classe, spazio dei nomi, proprietà o qualsiasi elemento necessario per il linguaggio in uso. Queste icone vengono usate in tutti gli elenchi IntelliSense, nella **barra di spostamento**e nella finestra attività **Elenco errori** . Per informazioni dettagliate, vedere la sezione "immagini del servizio di linguaggio" riportata di seguito.

## <a name="getlanguagepreferences-method"></a>Metodo GetLanguagePreferences
 Il <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> metodo restituisce sempre la stessa istanza di una <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. <xref:Microsoft.VisualStudio.Package.LanguagePreferences>Se non è necessaria alcuna preferenza aggiuntiva per il servizio di linguaggio, è possibile utilizzare la classe di base. Le classi del servizio di linguaggio MPF presuppongono la presenza di almeno la classe di base <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .

### <a name="example"></a>Esempio
 In questo esempio viene illustrata un'implementazione tipica del <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> metodo. In questo esempio viene utilizzata la classe di base <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(TestLanguageService).GUID,
                                                        this.Name );
                m_preferences.Init();
            }
            return m_preferences;
        }
    }
}
```

## <a name="getscanner-method"></a>Metodo GetScanner
 Questo metodo restituisce un'istanza di un <xref:Microsoft.VisualStudio.Package.IScanner> oggetto che implementa un parser o uno scanner orientato alla riga usato per ottenere i token e i relativi tipi e trigger. Questo scanner viene usato nella <xref:Microsoft.VisualStudio.Package.Colorizer> classe per la colorazione, sebbene lo scanner possa essere usato anche per ottenere i tipi di token e i trigger come preludio a un'operazione di analisi più complessa. È necessario fornire la classe che implementa l' <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia ed è necessario implementare tutti i metodi nell' <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia.

### <a name="example"></a>Esempio
 In questo esempio viene illustrata un'implementazione tipica del <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo. La `TestScanner` classe implementa l' <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia (non mostrata).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private TestScanner m_scanner;

        public override IScanner GetScanner(IVsTextLines buffer)
        {
            if (m_scanner == null)
            {
                m_scanner = new TestScanner(buffer);
            }
            return m_scanner;
        }
    }
}
    internal class TestScanner : IScanner
    {
        private IVsTextBuffer m_buffer;
        string m_source;

        public TestScanner(IVsTextBuffer buffer)
        {
            m_buffer = buffer;
        }

        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)
        {
            tokenInfo.Type = TokenType.Unknown;
            tokenInfo.Color = TokenColor.Text;
            return true;
        }

        void IScanner.SetSource(string source, int offset)
        {
            m_source = source.Substring(offset);
        }
    }

```

## <a name="parsesource-method"></a>Metodo ParseSource
 Analizza il file di origine in base a una serie di motivi diversi. A questo metodo viene assegnato un <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto che descrive il previsto da una particolare operazione di analisi. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo richiama un parser più complesso che determina la funzionalità e l'ambito del token. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo viene usato per supportare le operazioni di IntelliSense e per la corrispondenza tra parentesi graffe. Anche se non si supportano tali operazioni avanzate, è comunque necessario restituire un oggetto valido <xref:Microsoft.VisualStudio.Package.AuthoringScope> e che richiede la creazione di una classe che implementi l' <xref:Microsoft.VisualStudio.Package.AuthoringScope> interfaccia e implementi tutti i metodi su tale interfaccia. È possibile restituire valori null da tutti i metodi, ma l' <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto stesso non deve essere un valore null.

### <a name="example"></a>Esempio
 In questo esempio viene illustrata un'implementazione minima del <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo e della <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe, sufficiente per consentire al servizio di linguaggio di compilare e funzionare senza supportare effettivamente le funzionalità più avanzate.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            return new TestAuthoringScope();
        }
    }

    internal class TestAuthoringScope : AuthoringScope
    {
        public override string GetDataTipText(int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return null;
        }

        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Methods GetMethods(int line, int col, string name)
        {
            return null;
        }
}
```

## <a name="name-property"></a>Proprietà Name
 Questa proprietà restituisce il nome del servizio di linguaggio. Deve corrispondere al nome specificato quando il servizio di linguaggio è stato registrato. Questo nome viene usato in diversi punti, il più importante dei quali è la classe in <xref:Microsoft.VisualStudio.Package.LanguagePreferences> cui viene usato il nome per accedere al registro di sistema. Il nome restituito da questa proprietà non deve essere localizzato perché viene usato nel registro di sistema per la voce del registro di sistema e i nomi di chiave.

### <a name="example"></a>Esempio
 In questo esempio viene illustrata una possibile implementazione della <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> Proprietà. Si noti che il nome è hardcoded: il nome effettivo deve essere ottenuto da un file di risorse, in modo che possa essere usato per la registrazione di un servizio di linguaggio (vedere [registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override string Name
        {
            get { return "Test Language"; }
        }
    }
}
```

## <a name="instantiating-custom-classes"></a>Creazione di istanze di classi personalizzate
 È possibile eseguire l'override dei metodi seguenti nelle classi specificate per fornire istanze delle versioni personalizzate di ogni classe.

### <a name="in-the-languageservice-class"></a>Nella classe LanguageService

|Metodo|Classe restituita|Descrizione|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Per supportare aggiunte personalizzate alla visualizzazione di testo.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Per supportare le proprietà personalizzate del documento.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Per supportare la **barra di spostamento**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Per supportare funzioni nei modelli di frammenti di codice.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Per supportare i frammenti di codice (questo metodo non viene in genere sottoposto a override).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Per supportare la personalizzazione della <xref:Microsoft.VisualStudio.Package.ParseRequest> struttura (questo metodo non viene in genere sottoposto a override).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Per supportare la formattazione del codice sorgente, specificando i caratteri di commento e personalizzando le firme dei metodi.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Per supportare altri comandi di menu.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Per supportare l'evidenziazione della sintassi (questo metodo non viene in genere sottoposto a override).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Per supportare l'accesso alle preferenze della lingua. Questo metodo deve essere implementato ma può restituire un'istanza della classe di base.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Per fornire un parser utilizzato per identificare i tipi di token su una riga. Questo metodo deve essere implementato e <xref:Microsoft.VisualStudio.Package.IScanner> deve essere derivato da.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Per fornire un parser usato per identificare la funzionalità e l'ambito in un intero file di origine. Questo metodo deve essere implementato e deve restituire un'istanza della versione della <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe. Se si vuole supportare solo l'evidenziazione della sintassi (che richiede il <xref:Microsoft.VisualStudio.Package.IScanner> parser restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo), non è possibile eseguire alcuna operazione in questo metodo tranne che per restituire una versione della <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe i cui metodi restituiscono tutti valori null.|

### <a name="in-the-source-class"></a>Nella classe di origine

|Metodo|Classe restituita|Descrizione|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Per la personalizzazione della visualizzazione degli elenchi di completamento di IntelliSense (questo metodo non viene in genere sottoposto a override).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Per i marcatori di supporto nell'elenco attività Elenco errori; in particolare, il supporto per le funzionalità oltre l'apertura del file e il passaggio alla riga che ha causato l'errore.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Per personalizzare la visualizzazione delle descrizioni comandi delle informazioni sui parametri IntelliSense.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Per supportare il codice di commento.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Per la raccolta di informazioni durante l'operazione di analisi.|

### <a name="in-the-authoringscope-class"></a>Nella classe AuthoringScope

|Metodo|Classe restituita|Descrizione|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Fornisce un elenco di dichiarazioni, ad esempio membri o tipi. Questo metodo deve essere implementato ma può restituire un valore null. Se questo metodo restituisce un oggetto valido, l'oggetto deve essere un'istanza della versione della <xref:Microsoft.VisualStudio.Package.Declarations> classe.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Fornisce un elenco di firme del metodo per un contesto specificato. Questo metodo deve essere implementato ma può restituire un valore null. Se questo metodo restituisce un oggetto valido, l'oggetto deve essere un'istanza della versione della <xref:Microsoft.VisualStudio.Package.Methods> classe.|

## <a name="language-service-images"></a>Immagini del servizio di linguaggio
 Per fornire un elenco di icone da usare in tutto il servizio di linguaggio, eseguire l'override del <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe e restituire un oggetto <xref:System.Windows.Forms.ImageList> contenente le icone. La <xref:Microsoft.VisualStudio.Package.LanguageService> classe base carica un set predefinito di icone. Poiché si specifica l'indice dell'immagine esatto nelle posizioni che necessitano di icone, la modalità di disposizione dell'elenco di immagini è interamente all'utente.

### <a name="images-used-in-intellisense-completion-lists"></a>Immagini usate negli elenchi di completamento di IntelliSense
 Per gli elenchi di completamento di IntelliSense, l'indice dell'immagine viene specificato per ogni elemento nel <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> metodo della <xref:Microsoft.VisualStudio.Package.Declarations> classe, che è necessario eseguire l'override se si vuole fornire un indice di immagine. Il valore restituito dal <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> metodo è un indice nell'elenco di immagini fornito al costruttore della <xref:Microsoft.VisualStudio.Package.CompletionSet> classe e che è lo stesso elenco di immagini restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe (è possibile modificare l'elenco di immagini da usare per <xref:Microsoft.VisualStudio.Package.CompletionSet> se si esegue l'override del <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> metodo nella <xref:Microsoft.VisualStudio.Package.Source> classe per fornire un elenco di immagini diverso).

### <a name="images-used-in-the-navigation-bar"></a>Immagini utilizzate nella barra di spostamento
 La **barra di navigazione** Visualizza elenchi di tipi e membri e viene usata per la navigazione rapida può visualizzare le icone. Queste icone vengono ottenute dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe e non è possibile eseguirne l'override in modo specifico per la **barra di spostamento**. Gli indici utilizzati per ogni elemento nelle caselle combinate vengono specificati quando gli elenchi che rappresentano le caselle combinate vengono compilati nel <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo della <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe (vedere il [supporto per la barra di spostamento in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Questi indici di immagini vengono ottenuti in qualche modo dal parser, in genere tramite la versione della <xref:Microsoft.VisualStudio.Package.Declarations> classe. Il modo in cui vengono ottenuti gli indici dipende interamente dall'utente.

### <a name="images-used-in-the-error-list-task-window"></a>Immagini utilizzate nella finestra delle attività Elenco errori
 Ogni volta <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> che il parser del metodo (vedere il [parser e lo scanner del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) rileva un errore e passa tale errore al <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> metodo nella <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe, l'errore viene segnalato nella finestra delle attività **Elenco errori** . Un'icona può essere associata a ogni elemento visualizzato nella finestra attività e tale icona deriva dallo stesso elenco di immagini restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Il comportamento predefinito delle classi MPF è quello di non visualizzare un'immagine con il messaggio di errore. Tuttavia, è possibile eseguire l'override di questo comportamento derivando una classe dalla <xref:Microsoft.VisualStudio.Package.Source> classe ed eseguendo l'override del <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> metodo. In questo metodo si crea un nuovo <xref:Microsoft.VisualStudio.Package.DocumentTask> oggetto. Prima di restituire tale oggetto, è possibile usare la <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> proprietà nell' <xref:Microsoft.VisualStudio.Package.DocumentTask> oggetto per impostare l'indice dell'immagine. Si tratta di un aspetto simile all'esempio seguente. Si noti che `TestIconImageIndex` è un'enumerazione che elenca tutte le icone ed è specifica di questo esempio. È possibile che si disponga di un altro modo per identificare le icone nel servizio di linguaggio.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestSource : Source
    {
        public override DocumentTask CreateErrorTaskItem(
            TextSpan          span,
            string            filename,
            string            message,
            TaskPriority      priority,
            TaskCategory      category,
            MARKERTYPE        markerType,
            TaskErrorCategory errorCategory)
        {
            DocumentTask taskItem = base.CreateErrorTaskItem(
                                           span,
                                           filename,
                                           message,
                                           priority,
                                           category,
                                           markerType,
                                           errorCategory);
            if (errorCategory == TaskErrorCategory.Error)
            {
                taskItem.ImageIndex = TestIconImageIndex.Error;
            }
            return taskItem;
        }
    }
}
```

## <a name="the-default-image-list-for-a-language-service"></a>Elenco di immagini predefinito per un servizio di linguaggio
 L'elenco di immagini predefinito fornito con le classi del servizio di linguaggio MPF di base contiene una serie di icone associate agli elementi del linguaggio più comuni. La maggior parte di queste icone viene disposta in set di sei varianti, corrispondenti ai concetti di accesso di Public, Internal, Friend, protected, private e Shortcut. Ad esempio, è possibile avere icone diverse per un metodo a seconda che sia pubblico, protetto o privato.

 L'enumerazione seguente specifica i nomi tipici di ogni set di icone e specifica l'indice associato. Ad esempio, in base all'enumerazione, è possibile specificare l'indice dell'immagine per un metodo protetto come `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` . È possibile modificare i nomi in questa enumerazione come desiderato.

```csharp
public enum IconImageIndex
        {
            // access types
            AccessPublic = 0,
            AccessInternal = 1,
            AccessFriend = 2,
            AccessProtected = 3,
            AccessPrivate = 4,
            AccessShortcut = 5,

            Base = 6,
            // Each of the following icon type has 6 versions,
            //corresponding to the access types
            Class = Base + 0,
            Constant = Base + 1,
            Delegate = Base + 2,
            Enumeration = Base + 3,
            EnumMember = Base + 4,
            Event = Base + 5,
            Exception = Base + 6,
            Field = Base + 7,
            Interface = Base + 8,
            Macro = Base + 9,
            Map = Base + 10,
            MapItem = Base + 11,
            Method = Base + 12,
            OverloadedMethod = Base + 13,
            Module = Base + 14,
            Namespace = Base + 15,
            Operator = Base + 16,
            Property = Base + 17,
            Struct = Base + 18,
            Template = Base + 19,
            Typedef = Base + 20,
            Type = Base + 21,
            Union = Base + 22,
            Variable = Base + 23,
            ValueType = Base + 24,
            Intrinsic = Base + 25,
            JavaMethod = Base + 26,
            JavaField = Base + 27,
            JavaClass = Base + 28,
            JavaNamespace = Base + 29,
            JavaInterface = Base + 30,
            // Miscellaneous icons with one icon for each type.
            Error = 187,
            GreyedClass = 188,
            GreyedPrivateMethod = 189,
            GreyedProtectedMethod = 190,
            GreyedPublicMethod = 191,
            BrowseResourceFile = 192,
            Reference = 193,
            Library = 194,
            VBProject = 195,
            VBWebProject = 196,
            CSProject = 197,
            CSWebProject = 198,
            VB6Project = 199,
            CPlusProject = 200,
            Form = 201,
            OpenFolder = 202,
            ClosedFolder = 203,
            Arrow = 204,
            CSClass = 205,
            Snippet = 206,
            Keyword = 207,
            Info = 208,
            CallBrowserCall = 209,
            CallBrowserCallRecursive = 210,
            XMLEditor = 211,
            VJProject = 212,
            VJClass = 213,
            ForwardedType = 214,
            CallsTo = 215,
            CallsFrom = 216,
            Warning = 217,
        }
```

## <a name="see-also"></a>Vedere anche
- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Panoramica dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-overview.md)
- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Scanner e parser dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
