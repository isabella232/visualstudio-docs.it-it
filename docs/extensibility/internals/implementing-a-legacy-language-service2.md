---
title: Implementazione di un servizio di linguaggio Legacy2 . Documenti Microsoft
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
ms.openlocfilehash: e435af68a893c923eafef744762c9da8505c3fb7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707671"
---
# <a name="implementing-a-legacy-language-service"></a>Implementazione di un servizio di linguaggio legacy
Per implementare un servizio di linguaggio usando il framework del <xref:Microsoft.VisualStudio.Package.LanguageService> pacchetto gestito (MPF), è necessario derivare una classe dalla classe e implementare i metodi e le proprietà astratte seguenti:To implement a language service using the managed package framework (MPF), you must derive a class from the class and implement the following abstract methods and properties:

- Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- Proprietà <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Vedere le sezioni appropriate di seguito per informazioni dettagliate sull'implementazione di questi metodi e proprietà.

  Per supportare funzionalità aggiuntive, il servizio di linguaggio potrebbe essere necessario derivare una classe da una delle classi del servizio di linguaggio MPF; ad esempio, per supportare comandi di menu <xref:Microsoft.VisualStudio.Package.ViewFilter> aggiuntivi, è necessario derivare una <xref:Microsoft.VisualStudio.Package.ViewFilter> classe dalla classe ed eseguire l'override di diversi metodi di gestione dei comandi (vedere per informazioni dettagliate). La <xref:Microsoft.VisualStudio.Package.LanguageService> classe fornisce una serie di metodi che vengono chiamati per creare nuove istanze di varie classi ed eseguire l'override del metodo di creazione appropriato per fornire un'istanza della classe. Ad esempio, è necessario <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> eseguire <xref:Microsoft.VisualStudio.Package.LanguageService> l'override del metodo <xref:Microsoft.VisualStudio.Package.ViewFilter> nella classe per restituire un'istanza della propria classe. Vedere la sezione "Creazione di istanze di classi personalizzate" per ulteriori dettagli.

  Il servizio di linguaggio può anche fornire le proprie icone, che vengono utilizzate in molte posizioni. Ad esempio, quando viene visualizzato un elenco di completamento IntelliSense, a ogni elemento dell'elenco può essere associata un'icona, contrassegnando l'elemento come metodo, classe, spazio dei nomi, proprietà o qualsiasi elemento necessario per il linguaggio. Queste icone vengono utilizzate in tutti gli elenchi IntelliSense, nella **barra di spostamento**e nella finestra delle attività Elenco **errori.** Vedere la sezione "Immagini del servizio di linguaggio" di seguito per i dettagli.

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences Metodo
 Il <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> metodo restituisce sempre <xref:Microsoft.VisualStudio.Package.LanguagePreferences> la stessa istanza di una classe. È possibile utilizzare <xref:Microsoft.VisualStudio.Package.LanguagePreferences> la classe base se non sono necessarie preferenze aggiuntive per il servizio di linguaggio. Le classi del servizio di linguaggio MPF presuppongono la presenza di almeno la classe di base. <xref:Microsoft.VisualStudio.Package.LanguagePreferences>

### <a name="example"></a>Esempio
 In questo esempio viene <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> illustrata un'implementazione tipica del metodo. In questo esempio <xref:Microsoft.VisualStudio.Package.LanguagePreferences> viene utilizzata la classe base.

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
 Questo metodo restituisce <xref:Microsoft.VisualStudio.Package.IScanner> un'istanza di un oggetto che implementa un parser orientato alla riga o uno scanner utilizzato per ottenere i token e i relativi tipi e trigger. Questo scanner viene <xref:Microsoft.VisualStudio.Package.Colorizer> utilizzato nella classe per la colorazione, anche se lo scanner può essere utilizzato anche per ottenere tipi di token e trigger come preludio a un'operazione di analisi più complessa. È necessario fornire la <xref:Microsoft.VisualStudio.Package.IScanner> classe che implementa l'interfaccia <xref:Microsoft.VisualStudio.Package.IScanner> ed è necessario implementare tutti i metodi sull'interfaccia.

### <a name="example"></a>Esempio
 In questo esempio viene <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> illustrata un'implementazione tipica del metodo. La `TestScanner` classe <xref:Microsoft.VisualStudio.Package.IScanner> implementa l'interfaccia (non illustrata).

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
 Analizza il file di origine in base a diversi motivi. A questo metodo <xref:Microsoft.VisualStudio.Package.ParseRequest> viene assegnato un oggetto che descrive ciò che è previsto da una particolare operazione di analisi. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo richiama un parser più complesso che determina la funzionalità e l'ambito del token. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo viene utilizzato nel supporto per le operazioni IntelliSense, nonché la corrispondenza tra parentesi graffe. Anche se non si supportano tali operazioni avanzate, è comunque necessario restituire un oggetto valido <xref:Microsoft.VisualStudio.Package.AuthoringScope> e che richiede di creare una classe che implementa l'interfaccia <xref:Microsoft.VisualStudio.Package.AuthoringScope> e implementare tutti i metodi su tale interfaccia. È possibile restituire valori null <xref:Microsoft.VisualStudio.Package.AuthoringScope> da tutti i metodi, ma l'oggetto stesso non deve essere un valore null.

### <a name="example"></a>Esempio
 In questo esempio viene <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> illustrata <xref:Microsoft.VisualStudio.Package.AuthoringScope> un'implementazione minima del metodo e della classe, sufficiente per consentire al servizio di linguaggio di compilare e funzionare senza supportare effettivamente alcuna delle funzionalità più avanzate.

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
 Questa proprietà restituisce il nome del servizio di linguaggio. Deve essere lo stesso nome assegnato al momento della registrazione del servizio di linguaggio. Questo nome viene utilizzato in un certo numero di <xref:Microsoft.VisualStudio.Package.LanguagePreferences> posizioni, il più importante dei quali è la classe in cui il nome viene utilizzato per accedere al Registro di sistema. Il nome restituito da questa proprietà non deve essere localizzato in quanto viene utilizzato nel Registro di sistema per i nomi delle chiavi e delle voci del Registro di sistema.

### <a name="example"></a>Esempio
 In questo esempio viene <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> illustrata una possibile implementazione della proprietà. Si noti che il nome qui è hardcoded: il nome effettivo deve essere ottenuto da un file di risorse in modo che possa essere utilizzato nella registrazione di un servizio di linguaggio (vedere Registrazione di un servizio di [linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)).

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
 I metodi seguenti nelle classi specificate possono essere sottoposti a override per fornire istanze delle versioni personalizzate di ogni classe.

### <a name="in-the-languageservice-class"></a>Nella classe LanguageService

|Metodo|Classe restituita|Descrizione|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Per supportare aggiunte personalizzate alla visualizzazione di testo.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Per supportare le proprietà personalizzate del documento.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Per supportare la **barra di spostamento**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Per supportare le funzioni nei modelli di frammento di codice.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Per supportare i frammenti di codice (questo metodo in genere non viene sottoposto a override).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Per supportare <xref:Microsoft.VisualStudio.Package.ParseRequest> la personalizzazione della struttura (questo metodo in genere non viene sottoposto a override).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Per supportare la formattazione del codice sorgente, specificando i caratteri di commento e personalizzando le firme del metodo.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Per supportare comandi di menu aggiuntivi.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Per supportare l'evidenziazione della sintassi (questo metodo non viene in genere sottoposto a override).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Per supportare l'accesso alle preferenze della lingua. Questo metodo deve essere implementato ma può restituire un'istanza della classe base.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Per fornire un parser utilizzato per identificare i tipi di token su una riga. Questo metodo deve <xref:Microsoft.VisualStudio.Package.IScanner> essere implementato e deve essere derivato da.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Per fornire un parser utilizzato per identificare la funzionalità e l'ambito in un intero file di origine. Questo metodo deve essere implementato e deve restituire <xref:Microsoft.VisualStudio.Package.AuthoringScope> un'istanza della versione della classe. Se tutto ciò che si desidera <xref:Microsoft.VisualStudio.Package.IScanner> supportare è <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> l'evidenziazione della sintassi (che richiede il <xref:Microsoft.VisualStudio.Package.AuthoringScope> parser restituito dal metodo), non è possibile eseguire alcuna operazione in questo metodo se non restituire una versione della classe i cui metodi restituiscono tutti valori null.|

### <a name="in-the-source-class"></a>Nella classe di origine

|Metodo|Classe restituita|Descrizione|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Per personalizzare la visualizzazione degli elenchi di completamento IntelliSense (questo metodo in genere non viene sottoposto a override).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Per supportare i marcatori nell'elenco attività Elenco errori; in particolare, il supporto per le funzioni oltre l'apertura del file e il passaggio alla riga che ha causato l'errore.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Per personalizzare la visualizzazione delle descrizioni comandi delle informazioni sui parametri IntelliSense.For customizing the display of IntelliSense Parameter Info ToolTips.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Per supportare il codice dei commenti.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Per la raccolta di informazioni durante l'operazione di analisi.|

### <a name="in-the-authoringscope-class"></a>Nella classe AuthoringScope

|Metodo|Classe restituita|Descrizione|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Fornisce un elenco di dichiarazioni, ad esempio membri o tipi. Questo metodo deve essere implementato ma può restituire un valore null. Se questo metodo restituisce un oggetto valido, l'oggetto <xref:Microsoft.VisualStudio.Package.Declarations> deve essere un'istanza della versione della classe.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Fornisce un elenco di firme di metodo per un determinato contesto. Questo metodo deve essere implementato ma può restituire un valore null. Se questo metodo restituisce un oggetto valido, l'oggetto <xref:Microsoft.VisualStudio.Package.Methods> deve essere un'istanza della versione della classe.|

## <a name="language-service-images"></a>Immagini del servizio di linguaggio
 Per fornire un elenco di icone da utilizzare <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> in tutto <xref:Microsoft.VisualStudio.Package.LanguageService> il servizio <xref:System.Windows.Forms.ImageList> di linguaggio, eseguire l'override del metodo nella classe e restituire un contenente le icone. La <xref:Microsoft.VisualStudio.Package.LanguageService> classe base carica un set predefinito di icone. Dal momento che si specifica l'indice esatto dell'immagine in quei luoghi che necessitano di icone, come organizzare il proprio elenco di immagini è interamente a voi.

### <a name="images-used-in-intellisense-completion-lists"></a>Immagini utilizzate negli elenchi di completamento IntelliSenseImages Used In IntelliSense Completion Lists
 Per gli elenchi di completamento IntelliSense, l'indice dell'immagine viene specificato per ogni elemento nel <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> metodo della <xref:Microsoft.VisualStudio.Package.Declarations> classe , di cui è necessario eseguire l'override se si desidera fornire un indice di immagine. Il valore restituito <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> dal metodo è un indice nell'elenco di immagini fornito <xref:Microsoft.VisualStudio.Package.CompletionSet> al costruttore <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> della classe <xref:Microsoft.VisualStudio.Package.LanguageService> e che è lo stesso elenco <xref:Microsoft.VisualStudio.Package.CompletionSet> di immagini <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> restituito <xref:Microsoft.VisualStudio.Package.Source> dal metodo nella classe (è possibile modificare l'elenco di immagini da utilizzare per il se si esegue l'override del metodo nella classe per fornire un elenco di immagini diverso).

### <a name="images-used-in-the-navigation-bar"></a>Immagini utilizzate nella barra di navigazione
 La **barra di navigazione** visualizza elenchi di tipi e membri e viene utilizzata per la navigazione rapida può mostrare le icone. Queste icone vengono <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> ottenute <xref:Microsoft.VisualStudio.Package.LanguageService> dal metodo nella classe e non possono essere sottoposte a override in modo specifico per la **barra di spostamento**. Gli indici utilizzati per ogni elemento nelle caselle combinate vengono specificati quando <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> gli elenchi <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> che rappresentano le caselle combinate vengono compilati nel metodo nella classe (vedere Supporto per la barra di spostamento in un servizio di [linguaggio Legacy](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Questi indici di immagine vengono ottenuti in qualche modo <xref:Microsoft.VisualStudio.Package.Declarations> dal parser, in genere tramite la versione della classe. Il modo in cui gli indici si ottengono è interamente a voi.

### <a name="images-used-in-the-error-list-task-window"></a>Immagini utilizzate nella finestra delle attività Elenco errori
 Ogni <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> volta che il parser del metodo (vedere Parser e Scanner <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> del servizio <xref:Microsoft.VisualStudio.Package.AuthoringSink> di [linguaggio Legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) rileva un errore e lo passa al metodo nella classe, l'errore viene segnalato nella finestra dell'attività **Elenco errori.** Un'icona può essere associata a ogni elemento visualizzato nella finestra attività e tale <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> icona proviene dallo stesso elenco di immagini restituito dal metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Il comportamento predefinito delle classi MPF consiste nel non visualizzare un'immagine con il messaggio di errore. Tuttavia, è possibile eseguire l'override <xref:Microsoft.VisualStudio.Package.Source> di questo comportamento <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> derivando una classe dalla classe ed eseguendo l'override del metodo. In questo metodo, si <xref:Microsoft.VisualStudio.Package.DocumentTask> crea un nuovo oggetto. Prima di restituire tale oggetto, <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> è <xref:Microsoft.VisualStudio.Package.DocumentTask> possibile utilizzare la proprietà sull'oggetto per impostare l'indice dell'immagine. Questo sarebbe simile all'esempio seguente. Si `TestIconImageIndex` noti che è un'enumerazione che elenca tutte le icone ed è specifico per questo esempio. È possibile che nel servizio di linguaggio sia possibile identificare le icone in modo diverso.

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

## <a name="the-default-image-list-for-a-language-service"></a>Elenco immagini predefinito per un servizio di linguaggioThe Default Image List for a Language Service
 L'elenco di immagini predefinito fornito con le classi del servizio di linguaggio MPF di base contiene una serie di icone associate agli elementi del linguaggio più comuni. La maggior parte di queste icone sono disposte in set di sei varianti, corrispondenti ai concetti di accesso di pubblico, interno, amico, protetto, privato e scorciatoia. Ad esempio, è possibile avere icone diverse per un metodo a seconda che sia pubblico, protetto o privato.

 L'enumerazione seguente specifica i nomi tipici per ogni set di icone e specifica l'indice associato. Ad esempio, in base all'enumerazione, è possibile `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`specificare l'indice dell'immagine per un metodo protetto come . È possibile modificare i nomi in questa enumerazione come desiderato.

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
