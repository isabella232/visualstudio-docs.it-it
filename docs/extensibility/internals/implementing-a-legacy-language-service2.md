---
title: Implementazione di un servizio di linguaggio legacy2 | Microsoft Docs
description: Informazioni su come implementare un servizio di linguaggio legacy che supporta le funzionalità estese del servizio di linguaggio usando managed package framework (MPF). Parte 2 di 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fca2548ddb0c8281241b14de0ec470cfe22db1a1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900122"
---
# <a name="implementing-a-legacy-language-service-2"></a>Implementazione di un servizio di linguaggio legacy 2
Per implementare un servizio di linguaggio usando il framework del pacchetto gestito (MPF), è necessario derivare una classe dalla classe e implementare le proprietà e i metodi <xref:Microsoft.VisualStudio.Package.LanguageService> astratti seguenti:

- Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- Proprietà <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Per informazioni dettagliate sull'implementazione di questi metodi e proprietà, vedere le sezioni appropriate seguenti.

  Per supportare funzionalità aggiuntive, il servizio di linguaggio potrebbe essere necessario derivare una classe da una delle classi del servizio di linguaggio MPF. Ad esempio, per supportare comandi di menu aggiuntivi, è necessario derivare una classe dalla classe ed eseguire l'override di diversi metodi di gestione dei comandi <xref:Microsoft.VisualStudio.Package.ViewFilter> (vedere <xref:Microsoft.VisualStudio.Package.ViewFilter> per informazioni dettagliate). La classe fornisce diversi metodi chiamati per creare nuove istanze di varie classi ed eseguire l'override del metodo di creazione appropriato per fornire <xref:Microsoft.VisualStudio.Package.LanguageService> un'istanza della classe. Ad esempio, è necessario eseguire l'override del metodo nella classe per <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> restituire un'istanza della propria <xref:Microsoft.VisualStudio.Package.ViewFilter> classe. Per altre informazioni, vedere la sezione "Creazione di istanze di classi personalizzate".

  Il servizio di linguaggio può anche fornire le proprie icone, che vengono usate in molte posizioni. Ad esempio, quando viene visualizzato un elenco di completamento IntelliSense, a ogni elemento dell'elenco può essere associata un'icona, contrassegnando l'elemento come metodo, classe, spazio dei nomi, proprietà o qualsiasi elemento necessario per il linguaggio. Queste icone vengono usate in tutti gli elenchi di IntelliSense, nella barra **di** spostamento e nella **finestra attività Elenco** errori. Per informazioni dettagliate, vedere la sezione "Immagini del servizio di linguaggio" riportata di seguito.

## <a name="getlanguagepreferences-method"></a>Metodo GetLanguagePreferences
 Il <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> metodo restituisce sempre la stessa istanza di una classe <xref:Microsoft.VisualStudio.Package.LanguagePreferences> . È possibile usare la classe di base se non sono necessarie <xref:Microsoft.VisualStudio.Package.LanguagePreferences> preferenze aggiuntive per il servizio di linguaggio. Le classi del servizio di linguaggio MPF presuppongono la presenza almeno della classe di <xref:Microsoft.VisualStudio.Package.LanguagePreferences> base.

### <a name="example"></a>Esempio
 In questo esempio viene illustrata un'implementazione tipica del <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> metodo . In questo esempio viene utilizzata la classe di <xref:Microsoft.VisualStudio.Package.LanguagePreferences> base .

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
 Questo metodo restituisce un'istanza di un oggetto che implementa un parser o uno scanner orientato alla linea usato per ottenere i token e i <xref:Microsoft.VisualStudio.Package.IScanner> relativi tipi e trigger. Questo scanner viene usato nella classe per la colorazione, anche se lo scanner può essere usato anche per ottenere tipi di token e trigger come <xref:Microsoft.VisualStudio.Package.Colorizer> preludio a un'operazione di analisi più complessa. È necessario fornire la classe che implementa l'interfaccia ed è <xref:Microsoft.VisualStudio.Package.IScanner> necessario implementare tutti i metodi nell'interfaccia. <xref:Microsoft.VisualStudio.Package.IScanner>

### <a name="example"></a>Esempio
 In questo esempio viene illustrata un'implementazione tipica del <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo . La `TestScanner` classe implementa <xref:Microsoft.VisualStudio.Package.IScanner> l'interfaccia (non visualizzata).

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
 Analizza il file di origine in base a diversi motivi. A questo metodo viene assegnato <xref:Microsoft.VisualStudio.Package.ParseRequest> un oggetto che descrive ciò che è previsto da una particolare operazione di analisi. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo richiama un parser più complesso che determina la funzionalità del token e l'ambito. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo viene usato nel supporto per le operazioni IntelliSense e per la corrispondenza delle parentesi graffe. Anche se non si supportano tali operazioni avanzate, è comunque necessario restituire un oggetto valido e ciò richiede la creazione di una classe che implementa l'interfaccia e implementa tutti i metodi <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringScope> su tale interfaccia. È possibile restituire valori Null da tutti i metodi, ma <xref:Microsoft.VisualStudio.Package.AuthoringScope> l'oggetto stesso non deve essere un valore Null.

### <a name="example"></a>Esempio
 Questo esempio illustra un'implementazione minima del metodo e della classe , sufficiente per consentire al servizio di linguaggio di compilare e funzionare senza effettivamente supportare una delle <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> funzionalità più avanzate.

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
 Questa proprietà restituisce il nome del servizio di linguaggio. Deve essere lo stesso nome assegnato al momento della registrazione del servizio di linguaggio. Questo nome viene usato in diverse posizioni, la più importante delle quali è la classe in cui il nome viene <xref:Microsoft.VisualStudio.Package.LanguagePreferences> usato per accedere al Registro di sistema. Il nome restituito da questa proprietà non deve essere localizzato perché viene usato nel Registro di sistema per i nomi delle chiavi e delle voci del Registro di sistema.

### <a name="example"></a>Esempio
 In questo esempio viene illustrata una possibile implementazione della <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> proprietà . Si noti che il nome qui è hard-coded: il nome effettivo deve essere ottenuto da un file di risorse in modo che possa essere usato nella registrazione di un servizio di linguaggio (vedere Registrazione di un servizio di linguaggio [legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)).

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
 I metodi seguenti nelle classi specificate possono essere sottoposti a override per fornire istanze delle proprie versioni di ogni classe.

### <a name="in-the-languageservice-class"></a>Nella classe LanguageService

|Metodo|Classe restituita|Descrizione|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Per supportare aggiunte personalizzate alla visualizzazione testo.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Per supportare le proprietà personalizzate del documento.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Per supportare la **barra di spostamento**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Per supportare le funzioni nei modelli di frammento di codice.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Per supportare frammenti di codice (questo metodo in genere non viene sottoposto a override).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Per supportare la personalizzazione <xref:Microsoft.VisualStudio.Package.ParseRequest> della struttura (questo metodo in genere non viene sottoposto a override).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Per supportare la formattazione del codice sorgente, specificare i caratteri di commento e personalizzare le firme del metodo.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Per supportare comandi di menu aggiuntivi.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Per supportare l'evidenziazione della sintassi (questo metodo in genere non viene sottoposto a override).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Per supportare l'accesso alle preferenze della lingua. Questo metodo deve essere implementato ma può restituire un'istanza della classe di base.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Per fornire un parser usato per identificare i tipi di token in una riga. Questo metodo deve essere implementato e <xref:Microsoft.VisualStudio.Package.IScanner> deve essere derivato da .|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Per fornire un parser usato per identificare funzionalità e ambito in un intero file di origine. Questo metodo deve essere implementato e deve restituire un'istanza della versione della <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe . Se si vuole supportare solo l'evidenziazione della sintassi (che richiede il parser restituito dal metodo ), non è possibile eseguire alcuna operazione in questo metodo se non restituire una versione della classe i cui metodi restituiscono tutti valori <xref:Microsoft.VisualStudio.Package.IScanner> <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> Null.|

### <a name="in-the-source-class"></a>Nella classe source

|Metodo|Classe restituita|Descrizione|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Per la personalizzazione della visualizzazione degli elenchi di completamento IntelliSense (questo metodo in genere non viene sottoposto a override).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Per i marcatori di supporto nell'elenco attività Elenco errori; in particolare, il supporto per le funzionalità oltre ad aprire il file e passare alla riga che ha causato l'errore.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Per personalizzare la visualizzazione delle descrizioni comandi per le informazioni sui parametri di IntelliSense.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Per il supporto del codice di commento.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Per la raccolta di informazioni durante l'operazione di analisi.|

### <a name="in-the-authoringscope-class"></a>Nella classe AuthoringScope

|Metodo|Classe restituita|Descrizione|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Fornisce un elenco di dichiarazioni, ad esempio membri o tipi. Questo metodo deve essere implementato ma può restituire un valore Null. Se questo metodo restituisce un oggetto valido, l'oggetto deve essere un'istanza della versione della <xref:Microsoft.VisualStudio.Package.Declarations> classe .|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Fornisce un elenco di firme di metodo per un determinato contesto. Questo metodo deve essere implementato ma può restituire un valore Null. Se questo metodo restituisce un oggetto valido, l'oggetto deve essere un'istanza della versione della <xref:Microsoft.VisualStudio.Package.Methods> classe .|

## <a name="language-service-images"></a>Immagini del servizio di linguaggio
 Per fornire un elenco di icone da usare in tutto il servizio di linguaggio, eseguire l'override del metodo nella classe e <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> restituire un oggetto contenente le <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:System.Windows.Forms.ImageList> icone. La classe base <xref:Microsoft.VisualStudio.Package.LanguageService> carica un set predefinito di icone. Poiché si specifica l'indice esatto delle immagini in quelle posizioni che necessitano di icone, la modalità di disposizione dell'elenco di immagini dipende interamente dall'utente.

### <a name="images-used-in-intellisense-completion-lists"></a>Immagini usate negli elenchi di completamento IntelliSense
 Per gli elenchi di completamento IntelliSense, l'indice dell'immagine viene specificato per ogni elemento nel metodo della classe , di cui è necessario eseguire l'override se si vuole <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> fornire un indice di <xref:Microsoft.VisualStudio.Package.Declarations> immagine. Il valore restituito dal metodo è un indice nell'elenco di immagini fornito al costruttore della classe e che corrisponde allo stesso elenco di immagini restituito dal metodo nella classe . È possibile modificare l'elenco di immagini da usare per se si <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.CompletionSet> esegue <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.CompletionSet> l'override <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> <xref:Microsoft.VisualStudio.Package.Source> del metodo nella classe per fornire un elenco di immagini diverso.

### <a name="images-used-in-the-navigation-bar"></a>Immagini usate nella barra di spostamento
 La **barra di spostamento** visualizza gli elenchi di tipi e membri e viene usata per la navigazione rapida può visualizzare le icone. Queste icone vengono ottenute dal metodo nella classe e non possono essere sottoposte a override in modo <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> specifico per la barra di <xref:Microsoft.VisualStudio.Package.LanguageService> **spostamento.** Gli indici usati per ogni elemento nelle caselle combinate vengono specificati quando gli elenchi che rappresentano le caselle combinate vengono compilati nel metodo nella classe (vedere Supporto per la barra di spostamento in un servizio di linguaggio <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> [legacy).](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md) Questi indici di immagine vengono ottenuti in qualche modo dal parser, in genere tramite la versione della <xref:Microsoft.VisualStudio.Package.Declarations> classe . Il modo in cui si ottengono gli indici dipende interamente dall'utente.

### <a name="images-used-in-the-error-list-task-window"></a>Immagini usate nella finestra attività Elenco errori
 Ogni volta che il parser del metodo (vedere Parser e scanner del servizio di linguaggio legacy) rileva un errore e lo passa al metodo nella classe , l'errore viene segnalato nella finestra dell'attività Elenco <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> [](../../extensibility/internals/legacy-language-service-parser-and-scanner.md) <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink> errori.  Un'icona può essere associata a ogni elemento visualizzato nella finestra attività e tale icona proviene dallo stesso elenco di immagini restituito dal metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe . Il comportamento predefinito delle classi MPF è non visualizzare un'immagine con il messaggio di errore. Tuttavia, è possibile eseguire l'override di questo comportamento derivando una classe dalla <xref:Microsoft.VisualStudio.Package.Source> classe ed eseguendo l'override del <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> metodo . In questo metodo viene creato un nuovo <xref:Microsoft.VisualStudio.Package.DocumentTask> oggetto . Prima di restituire tale oggetto, è possibile usare la <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> proprietà <xref:Microsoft.VisualStudio.Package.DocumentTask> sull'oggetto per impostare l'indice dell'immagine. L'aspetto sarà simile all'esempio seguente. Si noti che `TestIconImageIndex` è un'enumerazione che elenca tutte le icone ed è specifica di questo esempio. È possibile che si abbia un modo diverso per identificare le icone nel servizio di linguaggio.

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
 L'elenco di immagini predefinito fornito con le classi del servizio di linguaggio MPF di base contiene una serie di icone associate agli elementi del linguaggio più comuni. La maggior parte di queste icone è disposta in set di sei varianti, corrispondenti ai concetti di accesso di public, internal, friend, protected, private e shortcut. Ad esempio, è possibile avere icone diverse per un metodo a seconda che sia pubblico, protetto o privato.

 L'enumerazione seguente specifica i nomi tipici per ogni set di icone e specifica l'indice associato. Ad esempio, in base all'enumerazione , è possibile specificare l'indice dell'immagine per un metodo protetto come `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` . È possibile modificare i nomi in questa enumerazione in base alle esigenze.

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
