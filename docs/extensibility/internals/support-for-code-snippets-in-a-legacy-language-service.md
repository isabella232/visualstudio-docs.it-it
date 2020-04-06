---
title: Supporto per frammenti di codice in un servizio di linguaggio Legacy Documenti Microsoft
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
ms.openlocfilehash: ad871eb73341f6ab87229687e2a6df898ffda32d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704916"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Supporto per i frammenti di codice in un servizio di linguaggio legacy
Un frammento di codice è una parte di codice che viene inserita nel file di origine. Il frammento stesso è un modello basato su XML con un set di campi. Questi campi vengono evidenziati dopo l'inserimento del frammento di codice e possono avere valori diversi a seconda del contesto in cui viene inserito il frammento. Immediatamente dopo l'inserimento del frammento, il servizio di linguaggio può formattare il frammento.

 Il frammento viene inserito in una modalità di modifica speciale che consente di spostarsi tra i campi del frammento utilizzando il tasto TAB. I campi possono supportare menu a discesa in stile IntelliSense.The fields can support IntelliSense-style drop-down menus. L'utente esegue il commit del frammento nel file di origine digitando il tasto INVIO o ESC. Per ulteriori informazioni sui frammenti di codice, vedere [Frammenti](../../ide/code-snippets.md)di codice .

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni, vedere [Procedura dettagliata: implementazione di frammenti](../../extensibility/walkthrough-implementing-code-snippets.md)di codice .

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

## <a name="managed-package-framework-support-for-code-snippets"></a>Supporto del framework del pacchetto gestito per i frammenti di codiceManaged Package Framework Support for Code Snippets
 Il framework del pacchetto gestito (MPF) supporta la maggior parte delle funzionalità dei frammenti, dalla lettura del modello all'inserimento del frammento e all'abilitazione della modalità di modifica speciale. Il supporto viene <xref:Microsoft.VisualStudio.Package.ExpansionProvider> gestito tramite la classe.

 Quando <xref:Microsoft.VisualStudio.Package.Source> viene creata un'istanza della <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> classe, il metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe viene chiamato per ottenere un <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto (si noti che la classe base <xref:Microsoft.VisualStudio.Package.LanguageService> restituisce sempre un nuovo <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto per ogni <xref:Microsoft.VisualStudio.Package.Source> oggetto).

 MPF non supporta le funzioni di espansione. Una funzione di espansione è una funzione denominata incorporata in un modello di frammento e restituisce uno o più valori da inserire in un campo. I valori vengono restituiti dal servizio <xref:Microsoft.VisualStudio.Package.ExpansionFunction> di linguaggio stesso tramite un oggetto . L'oggetto <xref:Microsoft.VisualStudio.Package.ExpansionFunction> deve essere implementato dal servizio di linguaggio per supportare le funzioni di espansione.

## <a name="providing-support-for-code-snippets"></a>Supporto per frammenti di codice
 Per abilitare il supporto per i frammenti di codice, è necessario fornire o installare i frammenti di codice ed è necessario fornire all'utente i mezzi per inserire tali frammenti. Esistono tre passaggi per abilitare il supporto per i frammenti di codice:There are three steps to enabling support for code snippets:

1. Installazione dei file di frammento.

2. Abilitazione dei frammenti di codice per il servizio di linguaggio.

3. Richiamare <xref:Microsoft.VisualStudio.Package.ExpansionProvider> l'oggetto.

### <a name="installing-the-snippet-files"></a>Installazione dei file di frammento
 Tutti i frammenti per un linguaggio vengono archiviati come modelli in file XML, in genere un modello di frammento per file. Per informazioni dettagliate sullo schema XML utilizzato per i modelli di frammento di codice, vedere Riferimento allo [schema dei frammenti di](../../ide/code-snippets-schema-reference.md)codice . Ogni modello di frammento viene identificato con un ID lingua. Questo ID lingua viene specificato nel Registro di sistema e viene inserito nell'attributo `Language` del tag \<Code> nel modello.

 Esistono in genere due posizioni in cui sono archiviati i file di modello di frammento: 1) in cui è stata installata la lingua e 2) nella cartella dell'utente. Questi percorsi vengono aggiunti al Registro di sistema in modo che Gestione **frammenti** di codice di Visual Studio possa trovare i frammenti. La cartella dell'utente è la posizione in cui vengono archiviati i frammenti creati dall'utente.

 Il layout di cartella tipico per i file di modello di frammento\\installati è simile al seguente: *[InstallRoot]*\\ *[TestLanguage]*-Snippets *[LCID]*- Frammenti.

 *[InstallRoot]* è la cartella in cui è installata la lingua.

 *[TestLanguage]* è il nome della lingua come nome di cartella.

 *[LCID]* è l'ID delle impostazioni locali. In questo modo vengono archiviate le versioni localizzate dei frammenti. Ad esempio, l'ID delle impostazioni locali per l'inglese è 1033, pertanto *[LCID]* viene sostituito da 1033.

 È necessario specificare un file aggiuntivo che è un file di indice, in genere denominato SnippetsIndex.xml o ExpansionsIndex.xml (è possibile utilizzare qualsiasi nome file valido che termina con .xml). Questo file viene in genere archiviato nella cartella *[InstallRoot]*\\ *[TestLanguage]* e specifica il percorso esatto della cartella dei frammenti, nonché l'ID lingua e il GUID del servizio di linguaggio che utilizza i frammenti. Il percorso esatto del file di indice viene inserito nel Registro di sistema come descritto più avanti in "Installazione delle voci del Registro di sistema". Di seguito è riportato un esempio di file SnippetsIndex.xml:Here is an example of a SnippetsIndex.xml file:

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

 Il \<tag Language> specifica l'ID lingua (l'attributo) `Lang` e il GUID del servizio di linguaggio.

 In questo esempio si presuppone che il servizio di linguaggio sia stato installato nella cartella di installazione di Visual Studio.This example assumes you have installed your language service in the Visual Studio installation folder. %LCID% viene sostituito con l'ID delle impostazioni locali corrente dell'utente. È \<possibile aggiungere più tag snippetDir>, uno per ogni directory e impostazioni locali diverse. Inoltre, una cartella di frammenti può contenere sottocartelle, ognuna delle quali è identificata nel file di indice con il \<tag> SnippetSubDir incorporato in un \<tag> SnippetDir.

 Gli utenti possono anche creare i propri snippet per la tua lingua. Questi sono in genere archiviati nella cartella delle impostazioni dell'utente,\\ad esempio *[TestDocs]*- Frammenti di codice *[TestLanguage]*- Test frammenti di codice, dove *[TestDocs]* è il percorso della cartella delle impostazioni dell'utente per Visual Studio.

 Gli elementi di sostituzione seguenti possono essere \<inseriti nel percorso archiviato nel tag dirPath> nel file di indice.

|Elemento|Descrizione|
|-------------|-----------------|
|%LCID%|ID delle impostazioni locali.|
|%InstallRoot%|Cartella di installazione radice per Visual Studio, ad esempio, C:.|
|%ProjDir%|Cartella contenente il progetto corrente.|
|%ProjItem%|Cartella contenente l'elemento di progetto corrente.|
|%TestDocs%|Cartella nella cartella delle impostazioni dell'utente, ad esempio\\ *[username]* C:.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Abilitazione dei frammenti di codice per il servizio di linguaggioEnabling Code Snippets for Your Language Service
 È possibile abilitare i frammenti di <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> codice per il servizio di linguaggio aggiungendo l'attributo al pacchetto VSPackage (vedere Registrazione di un servizio di [linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md) per i dettagli). I <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> parametri e sono facoltativi, `SearchPaths` ma è necessario includere il parametro denominato per informare **Gestione frammenti** di codice della posizione dei frammenti di codice.

 Di seguito è riportato un esempio di come utilizzare questo attributo:The following is an example of how to use this attribute:

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Chiamata al provider di espansioneCalling the Expansion Provider
 Il servizio di linguaggio controlla l'inserimento di qualsiasi frammento di codice, nonché il modo in cui viene richiamato l'inserimento.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Chiamata al provider di espansione per i frammenti di codiceCalling the Expansion Provider for Code Snippets
 Esistono due modi per richiamare il provider di espansione: utilizzando un comando di menu o utilizzando un collegamento da un elenco di completamento.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Inserimento di un frammento di codice tramite un comando di menuInserting a Code Snippet by using a Menu Command
 Per utilizzare un comando di menu per visualizzare il browser <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> frammento <xref:Microsoft.VisualStudio.Package.ExpansionProvider> di codice, aggiungere un comando di menu e quindi chiamare il metodo nell'interfaccia in risposta a tale comando di menu.

1. Aggiungere un comando e un pulsante al file vsct. Le istruzioni per eseguire questa operazione sono disponibili in [Creazione di un'estensione con un comando di menu](../../extensibility/creating-an-extension-with-a-menu-command.md).

2. Derivare una <xref:Microsoft.VisualStudio.Package.ViewFilter> classe dalla <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> classe ed eseguire l'override del metodo per indicare il supporto per il nuovo comando di menu. In questo esempio viene sempre abilitato il comando di menu.

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

3. Eseguire <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> l'override <xref:Microsoft.VisualStudio.Package.ViewFilter> del metodo <xref:Microsoft.VisualStudio.Package.ExpansionProvider> nella classe <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> per ottenere l'oggetto e chiamare il metodo su tale oggetto.

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

     I seguenti metodi <xref:Microsoft.VisualStudio.Package.ExpansionProvider> nella classe vengono chiamati da Visual Studio nell'ordine specificato durante il processo di inserimento del frammento di codice:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Dopo <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> la chiamata al metodo, il <xref:Microsoft.VisualStudio.Package.ExpansionProvider> frammento di codice è stato inserito e l'oggetto è in una speciale modalità di modifica utilizzata per modificare un frammento appena inserito.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Inserimento di un frammento di codice tramite un collegamento
 L'implementazione di un collegamento da un elenco di completamento è molto più complessa rispetto all'implementazione di un comando di menu. È innanzitutto necessario aggiungere collegamenti di frammento all'elenco di completamento delle parole IntelliSense.You must first add snippet shortcuts to the IntelliSense word completion list. Quindi è necessario rilevare quando un nome di collegamento frammento è stato inserito come risultato del completamento. Infine, è necessario ottenere il titolo e il percorso del <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> frammento <xref:Microsoft.VisualStudio.Package.ExpansionProvider> utilizzando il nome del collegamento e passare tali informazioni al metodo nel metodo .

 Per aggiungere collegamenti a frammenti all'elenco <xref:Microsoft.VisualStudio.Package.Declarations> di <xref:Microsoft.VisualStudio.Package.AuthoringScope> completamento delle parole, aggiungerli all'oggetto nella classe. È necessario assicurarsi che è possibile identificare il collegamento come un nome di frammento. Per un esempio, vedere [Procedura dettagliata: recupero di un elenco di frammenti di codice installati (implementazione legacy).](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 È possibile rilevare l'inserimento <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> del collegamento <xref:Microsoft.VisualStudio.Package.Declarations> del frammento di codice nel metodo della classe. Poiché il nome del frammento è già stato inserito nel file di origine, deve essere rimosso quando viene inserita l'espansione. Il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metodo accetta un intervallo che descrive il punto di inserimento per il frammento; se l'intervallo include l'intero nome del frammento nel file di origine, tale nome viene sostituito dal frammento.

 Ecco una versione <xref:Microsoft.VisualStudio.Package.Declarations> di una classe che gestisce l'inserimento di frammenti dato un nome di scelta rapida. Altri metodi <xref:Microsoft.VisualStudio.Package.Declarations> nella classe sono stati omessi per maggiore chiarezza. Si noti che il <xref:Microsoft.VisualStudio.Package.LanguageService> costruttore di questa classe accetta un oggetto. Questo può essere passato dalla <xref:Microsoft.VisualStudio.Package.AuthoringScope> versione dell'oggetto (ad <xref:Microsoft.VisualStudio.Package.AuthoringScope> esempio, l'implementazione della classe potrebbe prendere l'oggetto <xref:Microsoft.VisualStudio.Package.LanguageService> nel costruttore e passare tale oggetto al costruttore della `TestDeclarations` classe).

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

 Quando il servizio di linguaggio ottiene <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> il nome del collegamento, chiama il metodo per ottenere il nome del file e il titolo del frammento di codice. Il servizio di <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> linguaggio <xref:Microsoft.VisualStudio.Package.ExpansionProvider> chiama quindi il metodo nella classe per inserire il frammento di codice. I metodi seguenti vengono chiamati da Visual <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Studio nell'ordine specificato nella classe durante il processo di inserimento del frammento di codice:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Per ulteriori informazioni su come ottenere un elenco dei frammenti di codice installati per il servizio di linguaggio, vedere [procedura dettagliata: recupero di un elenco di frammenti di codice installati (implementazione legacy)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>Implementazione della classe ExpansionFunctionImplementing the ExpansionFunction Class
 Una funzione di espansione è una funzione denominata incorporata in un modello di frammento e restituisce uno o più valori da inserire in un campo. Per supportare le funzioni di espansione nel servizio di <xref:Microsoft.VisualStudio.Package.ExpansionFunction> linguaggio, <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> è necessario derivare una classe dalla classe e implementare il metodo. È quindi necessario <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> eseguire <xref:Microsoft.VisualStudio.Package.LanguageService> l'override del metodo nella classe per <xref:Microsoft.VisualStudio.Package.ExpansionFunction> restituire una nuova istanza della versione della classe per ogni funzione di espansione supportata. Se si supporta un elenco di valori possibili da <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> una funzione <xref:Microsoft.VisualStudio.Package.ExpansionFunction> di espansione, è necessario eseguire anche l'override del metodo nella classe per restituire un elenco di tali valori.

 Una funzione di espansione che accetta argomenti o deve accedere ad altri campi non deve essere associata a un campo modificabile, poiché il provider di espansione potrebbe non essere completamente inizializzato quando viene chiamata la funzione di espansione. Di conseguenza, la funzione di espansione non è in grado di ottenere il valore dei relativi argomenti o di qualsiasi altro campo.

### <a name="example"></a>Esempio
 Ecco un esempio di come una `GetName` funzione di espansione semplice chiamata potrebbe essere implementata. Questa funzione di espansione aggiunge un numero a un nome di classe base ogni volta che viene creata un'istanza della funzione di espansione (che corrisponde a ogni volta che viene inserito il frammento di codice associato).

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
- [Funzionalità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Frammenti di codiceCode Snippets](../../ide/code-snippets.md)
- [Procedura dettagliata: Recupero di un elenco di frammenti di codice installati (implementazione legacy)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
