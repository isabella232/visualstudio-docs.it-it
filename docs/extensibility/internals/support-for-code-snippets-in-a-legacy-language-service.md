---
title: Supporto per frammenti di codice in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni su come un servizio di linguaggio legacy supporta i frammenti di codice. Un frammento di codice è una porzione di codice che viene inserita nel file di origine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 781633a995027ee9938a0c579af32373c06207c2
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876610"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Supporto per i frammenti di codice in un servizio di linguaggio legacy
Un frammento di codice è una porzione di codice che viene inserita nel file di origine. Il frammento è un modello basato su XML con un set di campi. Questi campi vengono evidenziati dopo l'inserimento del frammento e possono avere valori diversi a seconda del contesto in cui viene inserito il frammento. Subito dopo l'inserimento del frammento di codice, il servizio di linguaggio può formattare il frammento.

 Il frammento viene inserito in una modalità di modifica speciale che consente di spostarsi tra i campi del frammento di codice utilizzando il tasto TAB. I campi possono supportare menu a discesa di tipo IntelliSense. L'utente effettua il commit del frammento di codice nel file di origine digitando il tasto invio o ESC. Per altre informazioni sui frammenti di codice, vedere [frammenti di codice](../../ide/code-snippets.md).

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni, vedere [procedura dettagliata: implementazione di frammenti di codice](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

## <a name="managed-package-framework-support-for-code-snippets"></a>Supporto del Framework di pacchetto gestito per i frammenti di codice
 Il Framework di pacchetto gestito (MPF) supporta la maggior parte delle funzionalità di frammento, leggendo il modello per inserire il frammento e abilitare la modalità di modifica speciale. Il supporto viene gestito tramite la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe.

 Quando <xref:Microsoft.VisualStudio.Package.Source> viene creata un'istanza della classe, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> viene chiamato il metodo della <xref:Microsoft.VisualStudio.Package.LanguageService> classe per ottenere un <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto. si noti che la <xref:Microsoft.VisualStudio.Package.LanguageService> classe di base restituisce sempre un nuovo <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto per ogni <xref:Microsoft.VisualStudio.Package.Source> oggetto.

 MPF non supporta le funzioni di espansione. Una funzione di espansione è una funzione denominata incorporata in un modello di frammento e restituisce uno o più valori da inserire in un campo. I valori vengono restituiti dal servizio di linguaggio stesso tramite un <xref:Microsoft.VisualStudio.Package.ExpansionFunction> oggetto. L' <xref:Microsoft.VisualStudio.Package.ExpansionFunction> oggetto deve essere implementato dal servizio di linguaggio per supportare le funzioni di espansione.

## <a name="providing-support-for-code-snippets"></a>Fornire supporto per frammenti di codice
 Per abilitare il supporto per i frammenti di codice, è necessario fornire o installare i frammenti di codice ed è necessario fornire agli utenti i mezzi per inserire tali frammenti. Sono disponibili tre passaggi per l'abilitazione del supporto per i frammenti di codice:

1. Installazione dei file di frammenti di codice.

2. Abilitazione dei frammenti di codice per il servizio di linguaggio.

3. Richiamo dell' <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto.

### <a name="installing-the-snippet-files"></a>Installazione dei file di frammento
 Tutti i frammenti per un linguaggio vengono archiviati come modelli nei file XML, in genere un modello di frammento per ogni file. Per informazioni dettagliate sul XML Schema usato per i modelli di frammenti di codice, vedere [riferimenti allo schema dei frammenti di codice](../../ide/code-snippets-schema-reference.md). Ogni modello di frammento viene identificato con un ID di lingua. Questo ID lingua viene specificato nel registro di sistema e inserito nell' `Language` attributo del \<Code> tag nel modello.

 In genere esistono due posizioni in cui sono archiviati i file di modello di frammento di codice: 1) in cui è stata installata la lingua e 2) nella cartella dell'utente. Questi percorsi vengono aggiunti al registro di sistema in modo che **Gestione frammenti di codice** di Visual Studio possa trovare i frammenti di codice. La cartella dell'utente è la posizione in cui vengono archiviati i frammenti di codice creati dall'utente.

 Il layout di cartella tipico per i file modello del frammento di codice installato ha un aspetto simile al seguente: *[InstallRoot]* \\ *[TestLanguage]* \Snippets \\ *[LCID]* \Snippets.

 *[InstallRoot]* è la cartella in cui è installato il linguaggio.

 *[TestLanguage]* è il nome della lingua come nome di cartella.

 *[LCID]* è l'ID delle impostazioni locali. Questo è il modo in cui vengono archiviate le versioni localizzate dei frammenti di codice. Ad esempio, l'ID delle impostazioni locali per l'inglese è 1033, quindi *[LCID]* viene sostituito da 1033.

 È necessario specificare un file aggiuntivo, ovvero un file di indice, generalmente denominato SnippetsIndex.xml o ExpansionsIndex.xml (è possibile utilizzare qualsiasi nome di file valido che termina con. Xml). Questo file viene in genere archiviato nella cartella *[InstallRoot]* \\ *[TestLanguage]* e specifica il percorso esatto della cartella dei frammenti di codice, nonché l'ID lingua e il GUID del servizio di linguaggio che utilizza i frammenti di codice. Il percorso esatto del file di indice viene inserito nel registro di sistema, come descritto più avanti in "installazione delle voci del registro di sistema". Di seguito è riportato un esempio di un file di SnippetsIndex.xml:

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

 Il \<Language> tag specifica l'ID lingua ( `Lang` attributo) e il GUID del servizio di linguaggio.

 Questo esempio presuppone che il servizio di linguaggio sia stato installato nella cartella di installazione di Visual Studio. % LCID% viene sostituito con l'ID delle impostazioni locali corrente dell'utente. \<SnippetDir>È possibile aggiungere più tag, uno per ogni directory e impostazioni locali diverse. Una cartella di frammenti può inoltre contenere sottocartelle, ognuna delle quali viene identificata nel file di indice con il \<SnippetSubDir> tag incorporato in un \<SnippetDir> tag.

 Gli utenti possono inoltre creare i propri frammenti di codice per il linguaggio. In genere vengono archiviati nella cartella delle impostazioni dell'utente, ad esempio *[TestDocs]* \code snippet \\ *[TestLanguage]* \test frammenti di codice, dove *[TestDocs]* è il percorso della cartella delle impostazioni dell'utente per Visual Studio.

 Gli elementi di sostituzione seguenti possono essere inseriti nel percorso archiviato nel \<DirPath> tag nel file di indice.

|Elemento|Descrizione|
|-------------|-----------------|
|LCID|ID delle impostazioni locali.|
|InstallRoot|Cartella di installazione radice per Visual Studio, ad esempio c:\Programmi\Microsoft Visual Studio 8.|
|%ProjDir%|Cartella contenente il progetto corrente.|
|%ProjItem%|Cartella contenente l'elemento del progetto corrente.|
|%TestDocs%|Cartella nella cartella delle impostazioni dell'utente, ad esempio C:\Documents and Settings \\ *[username]* \My Documenti\Visual Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Abilitazione dei frammenti di codice per il servizio di linguaggio
 È possibile abilitare i frammenti di codice per il servizio di linguaggio aggiungendo l' <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> attributo al pacchetto VSPackage. vedere la pagina relativa alla [registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md) per informazioni dettagliate. I <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> parametri e sono facoltativi, ma è necessario includere il `SearchPaths` parametro denominato per informare **Gestione frammenti di codice** della posizione dei frammenti di codice.

 Di seguito è riportato un esempio di utilizzo di questo attributo:

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Chiamata del provider di espansione
 Il servizio di linguaggio controlla l'inserimento di un frammento di codice, nonché il modo in cui viene richiamato l'inserimento.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Chiamata del provider di espansione per i frammenti di codice
 Esistono due modi per richiamare il provider di espansione: usando un comando di menu o un collegamento da un elenco di completamento.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Inserimento di un frammento di codice tramite un comando di menu
 Per usare un comando di menu per visualizzare il Visualizzatore dei frammenti di codice, aggiungere un comando di menu e quindi chiamare il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> metodo nell' <xref:Microsoft.VisualStudio.Package.ExpansionProvider> interfaccia in risposta a tale comando di menu.

1. Aggiungere un comando e un pulsante al file con estensione vsct. Per istruzioni su come eseguire questa operazione, vedere [creazione di un'estensione con un comando di menu](../../extensibility/creating-an-extension-with-a-menu-command.md).

2. Derivare una classe dalla <xref:Microsoft.VisualStudio.Package.ViewFilter> classe ed eseguire l'override del <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> metodo per indicare il supporto per il nuovo comando di menu. Questo esempio Abilita sempre il comando di menu.

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

3. Eseguire l'override del <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> metodo nella <xref:Microsoft.VisualStudio.Package.ViewFilter> classe per ottenere l' <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto e chiamare il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> metodo su tale oggetto.

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

     I metodi seguenti nella <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe vengono chiamati da Visual Studio nell'ordine indicato durante il processo di inserimento del frammento:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Dopo la <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> chiamata del metodo, il frammento è stato inserito e l' <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto si trova in una modalità di modifica speciale utilizzata per modificare un frammento appena inserito.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Inserimento di un frammento di codice tramite un collegamento
 L'implementazione di un collegamento da un elenco di completamento è molto più complessa rispetto all'implementazione di un comando di menu. È innanzitutto necessario aggiungere collegamenti al frammento di codice all'elenco di completamento delle parole IntelliSense. Sarà quindi necessario rilevare quando un nome di collegamento del frammento di codice è stato inserito come risultato del completamento. Infine, è necessario ottenere il titolo del frammento e il percorso usando il nome del collegamento e passare tali informazioni al <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metodo nel <xref:Microsoft.VisualStudio.Package.ExpansionProvider> metodo.

 Per aggiungere collegamenti al frammento di codice all'elenco di completamento delle parole, aggiungerli all' <xref:Microsoft.VisualStudio.Package.Declarations> oggetto nella <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe. È necessario assicurarsi di poter identificare il collegamento come nome di frammento. Per un esempio, vedere [procedura dettagliata: recupero di un elenco di frammenti di codice installati (implementazione legacy)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 È possibile rilevare l'inserimento del collegamento del frammento di codice nel <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> metodo della <xref:Microsoft.VisualStudio.Package.Declarations> classe. Poiché il nome del frammento è già stato inserito nel file di origine, è necessario rimuoverlo quando si inserisce l'espansione. Il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metodo accetta un intervallo che descrive il punto di inserimento per il frammento; se l'intervallo include l'intero nome del frammento nel file di origine, tale nome viene sostituito dal frammento.

 Di seguito è riportata una versione di una <xref:Microsoft.VisualStudio.Package.Declarations> classe che gestisce l'inserimento del frammento in base a un nome di collegamento. Altri metodi nella <xref:Microsoft.VisualStudio.Package.Declarations> classe sono stati omessi per maggiore chiarezza. Si noti che il costruttore di questa classe accetta un <xref:Microsoft.VisualStudio.Package.LanguageService> oggetto. Questo può essere passato dalla versione dell' <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto, ad esempio l'implementazione della <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe potrebbe portare l' <xref:Microsoft.VisualStudio.Package.LanguageService> oggetto nel costruttore e passare l'oggetto al `TestDeclarations` costruttore della classe.

```csharp
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

 Quando il servizio di linguaggio ottiene il nome del collegamento, chiama il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> metodo per ottenere il nome del file e il titolo del frammento di codice. Il servizio di linguaggio chiama quindi il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metodo nella <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe per inserire il frammento di codice. I metodi seguenti vengono chiamati da Visual Studio nell'ordine indicato nella <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe durante il processo di inserimento del frammento:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Per ulteriori informazioni su come ottenere un elenco dei frammenti di codice installati per il servizio di linguaggio, vedere [procedura dettagliata: recupero di un elenco di frammenti di codice installati (implementazione legacy)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>Implementazione della classe ExpansionFunction
 Una funzione di espansione è una funzione denominata incorporata in un modello di frammento e restituisce uno o più valori da inserire in un campo. Per supportare le funzioni di espansione nel servizio di linguaggio, è necessario derivare una classe dalla <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe e implementare il <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> metodo. È quindi necessario eseguire l'override del <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe per restituire una nuova istanza della versione della <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe per ogni funzione di espansione supportata. Se è supportato un elenco di valori possibili da una funzione di espansione, è necessario eseguire l'override anche del <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> metodo nella <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe per restituire un elenco di tali valori.

 Una funzione di espansione che accetta argomenti o deve accedere ad altri campi non deve essere associata a un campo modificabile, perché il provider di espansione potrebbe non essere completamente inizializzato dal momento in cui viene chiamata la funzione di espansione. Di conseguenza, la funzione di espansione non è in grado di ottenere il valore degli argomenti o di qualsiasi altro campo.

### <a name="example"></a>Esempio
 Di seguito è riportato un esempio di come è possibile implementare una funzione di espansione semplice denominata `GetName` . Questa funzione di espansione aggiunge un numero al nome di una classe di base ogni volta che viene creata un'istanza della funzione di espansione, che corrisponde a ogni volta che viene inserito il frammento di codice associato.

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

## <a name="see-also"></a>Vedi anche
- [Funzionalità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Frammenti di codice](../../ide/code-snippets.md)
- [Procedura dettagliata: Recupero di un elenco di frammenti di codice installati (implementazione legacy)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
