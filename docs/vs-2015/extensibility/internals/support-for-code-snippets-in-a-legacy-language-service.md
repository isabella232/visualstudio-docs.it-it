---
title: Supporto per i frammenti di codice in un servizio di linguaggio Legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8a96e6b10b68fc3b3275fbadb07de310c224da8c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104912"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Supporto per i frammenti di codice in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un frammento di codice è un frammento di codice che viene inserito nel file di origine. Il frammento di codice è un modello basato su XML con un set di campi. Questi campi vengono evidenziati dopo il frammento di codice viene inserito e può avere valori diversi a seconda del contesto in cui viene inserito il frammento di codice. Immediatamente dopo l'inserimento del frammento, il servizio di linguaggio possibile formattare il frammento di codice.  
  
 Il frammento di codice viene inserito in una modalità di modifica speciale che consente i campi del frammento di codice per spostarsi utilizzando il tasto TAB. I campi possono supportare i menu di IntelliSense in stile elenco a discesa. L'utente esegue il commit del frammento nel file di origine digitando l'invio o ESC. Per altre informazioni sui frammenti di codice, vedere [frammenti di codice](../../ide/code-snippets.md).  
  
 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni, vedere [procedura dettagliata: Implementazione di frammenti di codice](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>Supporto di Framework di pacchetto per frammenti di codice gestito  
 Il framework di pacchetto gestito (MPF) supporta la maggior parte delle funzionalità di frammento di codice, di leggere il modello a inserire il frammento di codice e consentendo la speciale modalità di modifica. Il supporto viene gestito tramite il <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe.  
  
 Quando la <xref:Microsoft.VisualStudio.Package.Source> viene creata un'istanza di classe, il <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe verrà chiamata per ottenere un' <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto (si noti che la base <xref:Microsoft.VisualStudio.Package.LanguageService> classe restituisce sempre un nuovo <xref:Microsoft.VisualStudio.Package.ExpansionProvider> per ciascun <xref:Microsoft.VisualStudio.Package.Source> oggetto).  
  
 MPF non supporta le funzioni di espansione. Una funzione di espansione è una funzione denominata che viene incorporata in un modello di frammento e restituisce uno o più valori da inserire in un campo. I valori vengono restituiti dal linguaggio di servizio stesso tramite un' <xref:Microsoft.VisualStudio.Package.ExpansionFunction> oggetto. Il <xref:Microsoft.VisualStudio.Package.ExpansionFunction> oggetto deve essere implementato dal servizio di linguaggio per supportare le funzioni di espansione.  
  
## <a name="providing-support-for-code-snippets"></a>Fornire il supporto per frammenti di codice  
 Per abilitare il supporto per frammenti di codice, è necessario fornire o installare i frammenti di codice ed è necessario fornire i mezzi per l'utente di inserire questi frammenti di codice. Esistono tre passaggi per abilitare il supporto per frammenti di codice:  
  
1. Installazione dei file di frammento di codice.  
  
2. Abilitazione di frammenti di codice per il servizio di linguaggio.  
  
3. Richiamare il <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto.  
  
### <a name="installing-the-snippet-files"></a>Installazione dei file di frammento di codice  
 Tutti i frammenti di codice per una lingua vengono archiviati come modelli in file XML, in genere un modello di frammento di codice per ogni file. Per informazioni dettagliate sullo schema XML usato per il modello di frammento di codice, vedere [riferimento dello Schema dei frammenti di codice](../../ide/code-snippets-schema-reference.md). Ogni modello di frammento di codice viene identificato con un ID lingua. Questo linguaggio ID viene specificato nel Registro di sistema e viene inserita la il `Language` attributo del \<codice > tag nel modello.  
  
 In genere esistono due posizioni in cui sono archiviati i file di modello di frammento di codice: 1) in cui è stata installata la lingua e 2) nella cartella dell'utente. Questi percorsi vengono aggiunti al Registro di sistema in modo che Visual Studio **Gestione frammenti di codice** possibile trovare i frammenti di codice. La cartella dell'utente è in cui sono archiviati frammenti di codice creati dall'utente.  
  
 Il layout cartella tipica per i file di modello di frammento di codice installati aspetto simile al seguente: *[elemento InstallRoot]*\\ *[TestLanguage]* \snippets.\\ *[LCID]* \Snippets.  
  
 *[Elemento InstallRoot]*  è la cartella del linguaggio è installato in.  
  
 *[TestLanguage]*  è il nome del linguaggio come nome di una cartella di.  
  
 *[LCID]*  è l'ID delle impostazioni locali. Si tratta di versioni localizzate come dei frammenti di codice vengono archiviate. Ad esempio, l'ID impostazioni locali per l'inglese è 1033, così *[LCID]* viene sostituito da 1033.  
  
 È necessario specificare un file aggiuntivo e che è un file di indice, in genere chiamato SnippetsIndex.xml o ExpansionsIndex.xml (è possibile usare qualsiasi nome di file valido che terminano con. XML). Questo file è in genere archiviato nel *[elemento InstallRoot]*\\ *[TestLanguage]* cartella e specifica la posizione esatta della cartella dei frammenti, nonché l'ID di lingua e il GUID del linguaggio servizio che utilizza i frammenti di codice. Il percorso esatto del file di indice viene inserito nel Registro di sistema come descritto più avanti in "Installare il voci del Registro di sistema". Di seguito è riportato un esempio di un file SnippetsIndex.xml:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<SnippetCollection>  
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">  
        <SnippetDir>  
            <OnOff>On</OnOff>  
            <Installed>true</Installed>  
            <Locale>1033</Locale>  
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>  
            <LocalizedName>Snippets</LocalizedName>  
        </SnippetDir>  
    </Language>  
</SnippetCollection>  
```  
  
 Il \<linguaggio > tag consente di specificare l'ID lingua (il `Lang` attributo) e il GUID del servizio di linguaggio.  
  
 Questo esempio si che è installato il servizio di linguaggio nella cartella di installazione di Visual Studio. La variabile % LCID % viene sostituita con l'ID impostazioni locali correnti. dell'utente Più \<SnippetDir > tag possono essere aggiunti, uno per ogni directory diverse e le impostazioni locali. Inoltre, una cartella di frammento può contenere le relative sottocartelle, ognuna delle quali è identificato nel file di indice con il \<SnippetSubDir > tag incorporati in un \<SnippetDir > tag.  
  
 Gli utenti possono anche creare i propri frammenti di codice per la propria lingua. Questi sono in genere archiviati nella cartella di impostazioni dell'utente, ad esempio *[TestDocs]* \Code frammenti\\ *[TestLanguage]* \Test frammenti di codice, in cui *[TestDocs]* è il percorso della cartella di impostazioni dell'utente per Visual Studio.  
  
 I seguenti elementi di sostituzione possono essere inseriti nel percorso memorizzato nel \<DirPath > tag nel file di indice.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|%LCID%|ID impostazioni locali.|  
|%InstallRoot%|Cartella di installazione radice per Visual Studio, ad esempio, C:\Program Files\Microsoft Visual Studio 8.|  
|%ProjDir%|Cartella contenente il progetto corrente.|  
|%ProjItem%|Cartella contenente l'elemento del progetto corrente.|  
|%TestDocs%|Nella cartella di impostazioni dell'utente, ad esempio, C:\Documents and Settings \\\ *[username]* \My Studio\8.|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>L'abilitazione di frammenti di codice per il servizio di linguaggio  
 È possibile abilitare i frammenti di codice per il servizio di linguaggio aggiungendo il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> dell'attributo per il pacchetto VSPackage (vedere [la registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md) per informazioni dettagliate). Il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> e <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> i parametri sono facoltativi, ma è consigliabile includere la `SearchPaths` parametro denominato per informare il **Gestione frammenti di codice** di percorso dei frammenti di codice.  
  
 Di seguito è riportato un esempio di come usare questo attributo:  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### <a name="calling-the-expansion-provider"></a>Chiamare il Provider di espansione  
 Il servizio di linguaggio controlla l'inserimento di ogni frammento di codice, nonché la modalità di inserimento viene richiamato.  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>Chiamare il Provider di espansione per frammenti di codice  
 Esistono due modi per richiamare il provider di espansione: usando un comando di menu o usando un collegamento da un elenco di completamento.  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Inserimento di un frammento di codice tramite un comando di Menu  
 Per usare un comando di menu da visualizzare nel browser del frammento di codice, aggiungere un comando di menu e quindi chiamare il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> nel metodo il <xref:Microsoft.VisualStudio.Package.ExpansionProvider> interfaccia in risposta a tale comando del menu.  
  
1. Aggiungere un comando e un pulsante al file con estensione vsct. È possibile trovare istruzioni per eseguire questa operazione nel [procedura dettagliata: Creazione di un comando di Menu tramite il modello di pacchetto di Visual Studio](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
2. Derivare una classe dal <xref:Microsoft.VisualStudio.Package.ViewFilter> classe ed eseguire l'override di <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> metodo per indicare il supporto per il nuovo comando di menu. Questo esempio Abilita sempre il comando di menu.  
  
    ```csharp  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)  
                : base(mgr, view)  
            {  
            }  
  
            protected override int QueryCommandStatus(ref Guid guidCmdGroup,  
                                                      uint nCmdId)  
            {  
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);  
                // If the base class did not recognize the command then  
                // see if we can handle the command.  
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)  
                {  
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                    {  
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                        {  
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);  
                        }  
                    }  
                }  
                return hr;  
            }  
        }  
    }  
    ```  
  
3. Eseguire l'override di <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> metodo nella <xref:Microsoft.VisualStudio.Package.ViewFilter> classe per ottenere il <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto e chiamare il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> metodo su tale oggetto.  
  
    ```csharp  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public override bool HandlePreExec(ref Guid guidCmdGroup,  
                                               uint nCmdId,  
                                               uint nCmdexecopt,  
                                               IntPtr pvaIn,  
                                               IntPtr pvaOut)  
            {  
                if (base.HandlePreExec(ref guidCmdGroup,  
                                       nCmdId,  
                                       nCmdexecopt,  
                                       pvaIn,  
                                       pvaOut))  
                {  
                    // Base class handled the command.  Do nothing more here.  
                    return true;  
                }  
  
                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                {  
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                    {  
                        ExpansionProvider ep = this.GetExpansionProvider();  
                        if (this.TextView != null && ep != null)  
                        {  
                            bool bDisplayed = ep.DisplayExpansionBrowser(  
                                this.TextView,  
                                "TestLanguagePackage Snippet:",  
                                null,  
                                false,  
                                null,  
                                false);  
                        }  
                        return true;   // Handled the command.  
                    }  
                }  
                return false;   // Did not handle the command.  
            }  
        }  
    }  
  
    ```  
  
     I metodi seguenti il <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe vengono chiamati nell'ordine specificato durante il processo di inserimento del frammento da Visual Studio:  
  
4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     Dopo il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> viene chiamato il metodo, è stato inserito il frammento di codice e <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto è una speciale modalità di modifica utilizzata per la modifica di un frammento di codice che è appena stato inserito.  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Inserimento di un frammento di codice tramite un collegamento  
 Implementazione di un collegamento da un elenco di completamento è molto più complessa rispetto all'implementazione di un comando di menu. È innanzitutto necessario aggiungere collegamenti dei frammenti di all'elenco di completamento IntelliSense word. È quindi necessario rilevare quando un nome di scelta rapida del frammento di codice è stato inserito come risultato di completamento. Infine, è necessario ottenere il titolo di frammento di codice e il percorso usando il nome del collegamento e passare tali informazioni per il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metodo su di <xref:Microsoft.VisualStudio.Package.ExpansionProvider> (metodo).  
  
 Per aggiungere collegamenti dei frammenti per l'elenco di completamento di word, aggiungerli per il <xref:Microsoft.VisualStudio.Package.Declarations> dell'oggetto nel <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe. È necessario assicurarsi che è possibile identificare il collegamento come nome di frammento di codice. Per un esempio, vedere [Procedura dettagliata: Come ottenere un elenco di installato i frammenti di codice (implementazione Legacy)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 È possibile rilevare l'inserimento del collegamento del frammento di codice nel <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> metodo di <xref:Microsoft.VisualStudio.Package.Declarations> classe. Poiché il nome del frammento di codice è già stato inserito nel file di origine, è necessario innanzitutto rimuoverlo quando viene inserita l'espansione. Il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metodo accetta un intervallo che descrive il punto di inserimento per il frammento di codice; se l'intervallo include il nome intero frammento di codice nel file di origine, tale nome viene sostituito dal frammento.  
  
 Di seguito è una versione di un <xref:Microsoft.VisualStudio.Package.Declarations> classe che gestisce l'inserimento del frammento assegnato un nome di scelta rapida. Altri metodi di <xref:Microsoft.VisualStudio.Package.Declarations> classe sono stati omessi per maggiore chiarezza. Si noti che il costruttore di questa classe accetta un <xref:Microsoft.VisualStudio.Package.LanguageService> oggetto. Ciò può essere passato dalla versione del <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto (ad esempio, l'implementazione del <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe potrebbe richiedere il <xref:Microsoft.VisualStudio.Package.LanguageService> nel relativo costruttore, quindi passare tale oggetto al `TestDeclarations` costruttore della classe).  
  
```  
[C#]  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList       declarations;  
        private LanguageService languageService;  
        private TextSpan        commitSpan;  
  
        public TestDeclarations(LanguageService langService)  
            : base()  
        {  
            languageService = langService;  
            declarations = new ArrayList();  
        }  
  
        // This method is used to add declarations to the internal list.  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        // This method is called to get the string to commit to the source buffer.  
        // Note that the initial extent is only what the user has typed so far.  
        public override string OnCommit(IVsTextView textView,  
                                        string textSoFar,  
                                        char commitCharacter,  
                                        int index,  
                                        ref TextSpan initialExtent)  
        {  
            // We intercept this call only to get the initial extent  
            // of what was committed to the source buffer.  
            commitSpan = initialExtent;  
  
            return base.OnCommit(textView,  
                                 textSoFar,  
                                 commitCharacter,  
                                 index,  
                                 ref initialExtent);  
        }  
  
        // This method is called after the string has been committed to the source buffer.  
        public override char OnAutoComplete(IVsTextView textView,  
                                            string committedText,  
                                            char commitCharacter,  
                                            int index)  
        {  
            TestDeclaration item = declarations[index] as TestDeclaration;  
            if (item != null)  
            {  
                // In this example, TestDeclaration identifies types with a string.  
                // You can choose a different approach.  
                if (item.Type == "snippet")  
                {  
                    Source src = languageService.GetSource(textView);  
                    if (src != null)  
                    {  
                        ExpansionProvider ep = src.GetExpansionProvider();  
                        if (ep != null)  
                        {  
                            string title;  
                            string path;  
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;  
                            if (commitLength < committedText.Length)  
                            {  
                                // Replace everything that was inserted  
                                // so calculate the span of the full  
                                // insertion, taking into account what  
                                // was inserted when the commitSpan  
                                // was obtained in the first place.  
                                commitSpan.iEndIndex += (committedText.Length - commitLength);  
                            }  
  
                            if (ep.FindExpansionByShortcut(textView,  
                                                           committedText,  
                                                           commitSpan,  
                                                           true,  
                                                           out title,  
                                                           out path))  
                            {  
                                ep.InsertNamedExpansion(textView,  
                                                        title,  
                                                        path,  
                                                        commitSpan,  
                                                        false);  
                            }  
                        }  
                    }  
                }  
            }  
            return '\0';  
        }  
    }  
}  
```  
  
 Quando il servizio di linguaggio Ottiene il nome del collegamento, chiama il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> metodo per ottenere il titolo del frammento di codice filename e codice. Chiama quindi il servizio di linguaggio il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> nel metodo il <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe per inserire il frammento di codice. I seguenti metodi vengono chiamati da Visual Studio nell'ordine indicato nel <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe durante il processo di inserimento del frammento:  
  
1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
   Per altre informazioni su come ottenere un elenco di frammenti di codice installati per il servizio di linguaggio, vedere [procedura dettagliata: Come ottenere un elenco di installato i frammenti di codice (implementazione Legacy)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## <a name="implementing-the-expansionfunction-class"></a>Implementazione della classe ExpansionFunction  
 Una funzione di espansione è una funzione denominata che viene incorporata in un modello di frammento e restituisce uno o più valori da inserire in un campo. Per supportare le funzioni di espansione nel servizio di linguaggio, è necessario derivare una classe dalla classe la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe e implementare il <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> (metodo). È quindi necessario eseguire l'override di <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe per restituire un'istanza nuova della versione del <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe per ogni funzione di espansione è supportare. Se si supporta un elenco di valori possibili da una funzione di espansione, è inoltre necessario sostituire il <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> nel metodo il <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe per restituire un elenco di tali valori.  
  
 Una funzione di espansione che accetta argomenti o richiede l'accesso ad altri campi non deve essere associata a un campo modificabile, come il provider di espansione potrebbe non essere inizializzato completamente entro l'ora che viene chiamata la funzione di espansione. Di conseguenza, la funzione di espansione non è in grado di ottenere il valore dei relativi argomenti o qualsiasi altro campo.  
  
### <a name="example"></a>Esempio  
 Di seguito è riportato un esempio di come chiamata una funzione di espansione semplice `GetName` può essere implementato. Questa funzione di espansione viene aggiunto un numero a un nome di classe di base a ogni volta che viene creata la funzione di espansione (che corrisponde a ogni volta che il frammento di codice associato viene inserita).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private int classNameCounter = 0;  
  
        public override ExpansionFunction CreateExpansionFunction(  
            ExpansionProvider provider,  
            string functionName)  
        {  
            ExpansionFunction function = null;  
            if (functionName == "GetName")  
            {  
                ++classNameCounter;  
                function = new TestGetNameExpansionFunction(provider, classNameCounter);  
            }  
            return function;  
        }  
    }  
  
    internal class TestGetNameExpansionFunction : ExpansionFunction  
    {  
        private int nameCount;  
  
        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)  
            : base(provider)  
        {  
            nameCount = counter;  
        }  
  
        public override string GetCurrentValue()  
        {  
            string name = "TestClass";  
            name += nameCount.ToString();  
            return name;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)   
 [La registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Frammenti di codice](../../ide/code-snippets.md)   
 [Procedura dettagliata: Come ottenere un elenco di frammenti di codice installati (implementazione Legacy)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
