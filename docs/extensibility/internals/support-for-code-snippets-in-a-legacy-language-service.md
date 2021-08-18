---
title: Supporto per frammenti di codice in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni su come un servizio di linguaggio legacy supporta frammenti di codice. Un frammento di codice è una parte di codice inserita nel file di origine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 71d12bb0bd80c10140aaaa6f276cf772397d699f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086612"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Supporto per i frammenti di codice in un servizio di linguaggio legacy
Un frammento di codice è una parte di codice inserita nel file di origine. Il frammento di codice è un modello basato su XML con un set di campi. Questi campi vengono evidenziati dopo l'inserimento del frammento di codice e possono avere valori diversi a seconda del contesto in cui viene inserito il frammento di codice. Subito dopo l'inserimento del frammento di codice, il servizio di linguaggio può formattare il frammento di codice.

 Il frammento di codice viene inserito in una modalità di modifica speciale che consente di spostarsi tra i campi del frammento di codice usando il tasto TAB. I campi possono supportare menu a discesa in stile IntelliSense. L'utente esegue il commit del frammento di codice nel file di origine digitando il tasto INVIO o ESC. Per altre informazioni sui frammenti di codice, vedere [Frammenti di codice](../../ide/code-snippets.md).

 I servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni, vedere [Procedura dettagliata: Implementazione di frammenti di codice](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. In questo modo si miglioreranno le prestazioni del servizio di linguaggio e si potranno sfruttare le nuove funzionalità dell'editor.

## <a name="managed-package-framework-support-for-code-snippets"></a>Supporto del framework del pacchetto gestito per frammenti di codice
 Il framework del pacchetto gestito (MPF) supporta la maggior parte delle funzionalità dei frammenti, dalla lettura del modello all'inserimento del frammento di codice e all'abilitazione della modalità di modifica speciale. Il supporto viene gestito tramite la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe .

 Quando viene creata un'istanza della classe, viene chiamato il metodo nella classe per ottenere un oggetto . Si noti che la classe base restituisce sempre un nuovo oggetto <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> per ogni <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.ExpansionProvider> <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.ExpansionProvider> <xref:Microsoft.VisualStudio.Package.Source> oggetto.

 MPF non supporta le funzioni di espansione. Una funzione di espansione è una funzione denominata incorporata in un modello di frammento di codice e restituisce uno o più valori da inserire in un campo. I valori vengono restituiti dal servizio di linguaggio stesso tramite un <xref:Microsoft.VisualStudio.Package.ExpansionFunction> oggetto . <xref:Microsoft.VisualStudio.Package.ExpansionFunction>L'oggetto deve essere implementato dal servizio di linguaggio per supportare le funzioni di espansione.

## <a name="providing-support-for-code-snippets"></a>Supporto per frammenti di codice
 Per abilitare il supporto per i frammenti di codice, è necessario fornire o installare i frammenti di codice ed è necessario fornire all'utente i mezzi per inserire tali frammenti. Per abilitare il supporto per i frammenti di codice, è necessario eseguire tre passaggi:

1. Installazione dei file di frammento di codice.

2. Abilitazione di frammenti di codice per il servizio di linguaggio.

3. Chiamata <xref:Microsoft.VisualStudio.Package.ExpansionProvider> dell'oggetto .

### <a name="installing-the-snippet-files"></a>Installazione dei file di frammento di codice
 Tutti i frammenti di codice per un linguaggio vengono archiviati come modelli in file XML, in genere un modello di frammento per ogni file. Per informazioni dettagliate sullo schema XML usato per i modelli di frammenti di codice, vedere [Informazioni di riferimento sullo schema dei frammenti di codice](../../ide/code-snippets-schema-reference.md). Ogni modello di frammento di codice viene identificato con un ID lingua. Questo ID lingua viene specificato nel Registro di sistema e inserito `Language` nell'attributo del tag nel \<Code> modello.

 In genere sono archiviati i file modello di frammento di codice in due posizioni: 1) in cui è stata installata la lingua e 2) nella cartella dell'utente. Questi percorsi vengono aggiunti al Registro di sistema in modo che Visual Studio **Gestione frammenti di** codice possa trovare i frammenti di codice. La cartella dell'utente è la posizione in cui vengono archiviati i frammenti creati dall'utente.

 Il layout di cartella tipico per i file modello di frammento di codice installato è simile al seguente: *[InstallRoot]* \\ *[TestLanguage]* \Snippets \\ *[LCID]* \Snippets.

 *[InstallRoot]* è la cartella in cui è installata la lingua.

 *[TestLanguage]* è il nome della lingua come nome di cartella.

 *[LCID] è* l'ID delle impostazioni locali. In questo modo vengono archiviate le versioni localizzate dei frammenti di codice. Ad esempio, l'ID delle impostazioni locali per l'inglese è 1033, quindi *[LCID]* viene sostituito da 1033.

 È necessario specificare un file aggiuntivo, ovvero un file di indice, in genere denominato SnippetsIndex.xml o ExpansionsIndex.xml (è possibile usare qualsiasi nome file valido che termina con .xml). Questo file viene in genere archiviato nella cartella *[InstallRoot]* \\ *[TestLanguage]* e specifica il percorso esatto della cartella dei frammenti di codice, nonché l'ID lingua e il GUID del servizio di linguaggio che usa i frammenti di codice. Il percorso esatto del file di indice viene inserito nel Registro di sistema come descritto più avanti in "Installazione delle voci del Registro di sistema". Di seguito è riportato un esempio di SnippetsIndex.xml file:

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

 Il \<Language> tag specifica l'ID lingua (l'attributo) `Lang` e il GUID del servizio di linguaggio.

 In questo esempio si presuppone che il servizio di linguaggio sia stato installato nella Visual Studio di installazione. %LCID% viene sostituito con l'ID impostazioni locali corrente dell'utente. È \<SnippetDir> possibile aggiungere più tag, uno per ogni directory e impostazioni locali diverse. Inoltre, una cartella di frammenti di codice può contenere sottocartelle, ognuna delle quali è identificata nel file di indice con \<SnippetSubDir> il tag incorporato in un \<SnippetDir> tag.

 Gli utenti possono anche creare frammenti di codice personalizzati per il linguaggio. Questi file vengono in genere archiviati nella cartella delle impostazioni dell'utente, ad esempio *[TestDocs]* \Frammenti di codice \\ *[TestLanguage]* \Frammenti di codice di test, dove *[TestDocs]* è il percorso della cartella delle impostazioni dell'utente per Visual Studio.

 Gli elementi di sostituzione seguenti possono essere inseriti nel percorso archiviato nel \<DirPath> tag nel file di indice.

|Elemento|Descrizione|
|-------------|-----------------|
|%LCID%|ID delle impostazioni locali.|
|%InstallRoot%|Cartella di installazione radice per Visual Studio, ad esempio C:\Programmi\Microsoft Visual Studio 8.|
|%ProjDir%|Cartella contenente il progetto corrente.|
|%ProjItem%|Cartella contenente l'elemento di progetto corrente.|
|%TestDocs%|Cartella nella cartella delle impostazioni dell'utente, ad esempio C:\Documents e Impostazioni \\ *[nome utente]* \Documenti\Visual Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Abilitazione di frammenti di codice per il servizio di linguaggio
 È possibile abilitare i frammenti di codice per il servizio di linguaggio aggiungendo l'attributo al pacchetto VSPackage . Per informazioni dettagliate, vedere Registrazione di un servizio <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> [di linguaggio](../../extensibility/internals/registering-a-legacy-language-service1.md) legacy. I parametri e sono facoltativi, ma è necessario includere il parametro denominato per informare Gestione frammenti di codice del <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> percorso dei `SearchPaths` frammenti di codice. 

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

### <a name="calling-the-expansion-provider"></a>Chiamata del provider di espansione
 Il servizio di linguaggio controlla l'inserimento di qualsiasi frammento di codice, nonché il modo in cui viene richiamato l'inserimento.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Chiamata del provider di espansione per frammenti di codice
 Esistono due modi per richiamare il provider di espansione: usando un comando di menu o un collegamento da un elenco di completamento.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Inserimento di un frammento di codice tramite un comando di menu
 Per usare un comando di menu per visualizzare il browser dei frammenti di codice, aggiungere un comando di menu e quindi chiamare il metodo nell'interfaccia <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> in risposta a tale comando di <xref:Microsoft.VisualStudio.Package.ExpansionProvider> menu.

1. Aggiungere un comando e un pulsante al file con estensione vsct. Per istruzioni, vedere Creazione di [un'estensione con un comando di menu](../../extensibility/creating-an-extension-with-a-menu-command.md).

2. Derivare una classe dalla <xref:Microsoft.VisualStudio.Package.ViewFilter> classe ed eseguire l'override <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> del metodo per indicare il supporto per il nuovo comando di menu. Questo esempio abilita sempre il comando di menu.

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

3. Eseguire <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> l'override del metodo <xref:Microsoft.VisualStudio.Package.ViewFilter> nella classe per ottenere <xref:Microsoft.VisualStudio.Package.ExpansionProvider> l'oggetto e chiamare <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> il metodo su tale oggetto.

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

     I metodi seguenti nella <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe vengono chiamati da Visual Studio nell'ordine specificato durante il processo di inserimento del frammento di codice:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Dopo la chiamata al metodo , il frammento di codice è stato inserito e l'oggetto è in una modalità di modifica speciale usata per modificare un frammento <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> <xref:Microsoft.VisualStudio.Package.ExpansionProvider> appena inserito.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Inserimento di un frammento di codice tramite un collegamento
 L'implementazione di un collegamento da un elenco di completamento è molto più coinvolta rispetto all'implementazione di un comando di menu. È prima necessario aggiungere collegamenti ai frammenti di codice all'elenco di completamento delle parole intelliSense. È quindi necessario rilevare quando un nome di collegamento del frammento è stato inserito come risultato del completamento. Infine, è necessario ottenere il titolo e il percorso del frammento di codice usando il nome del collegamento e passare queste informazioni al <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metodo nel <xref:Microsoft.VisualStudio.Package.ExpansionProvider> metodo .

 Per aggiungere collegamenti ai frammenti di codice all'elenco di completamento delle parole, aggiungerli <xref:Microsoft.VisualStudio.Package.Declarations> all'oggetto nella <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe . È necessario assicurarsi di poter identificare il collegamento come nome di frammento di codice. Per un esempio, vedere [Procedura dettagliata: Recupero di un elenco di frammenti di codice installati (implementazione legacy).](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 È possibile rilevare l'inserimento del collegamento del frammento di codice nel <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> metodo della <xref:Microsoft.VisualStudio.Package.Declarations> classe . Poiché il nome del frammento di codice è già stato inserito nel file di origine, deve essere rimosso quando viene inserita l'espansione. Il metodo accetta un intervallo che descrive il punto di inserimento per il frammento di codice. Se l'intervallo include l'intero nome del frammento nel file di origine, tale nome viene <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> sostituito dal frammento di codice.

 Ecco una versione di una classe che gestisce <xref:Microsoft.VisualStudio.Package.Declarations> l'inserimento di frammenti di codice in base a un nome di collegamento. Altri metodi nella <xref:Microsoft.VisualStudio.Package.Declarations> classe sono stati omessi per maggiore chiarezza. Si noti che il costruttore di questa classe accetta un <xref:Microsoft.VisualStudio.Package.LanguageService> oggetto . Questo può essere passato dalla versione dell'oggetto (ad esempio, l'implementazione della classe potrebbe prendere l'oggetto nel costruttore e passare tale oggetto al costruttore <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringScope> della <xref:Microsoft.VisualStudio.Package.LanguageService> `TestDeclarations` classe).

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

 Quando il servizio di linguaggio ottiene il nome del collegamento, chiama il metodo per ottenere il nome file e il titolo del <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> frammento di codice. Il servizio di linguaggio chiama quindi il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metodo nella classe per inserire il <xref:Microsoft.VisualStudio.Package.ExpansionProvider> frammento di codice. I metodi seguenti vengono chiamati da Visual Studio nell'ordine specificato nella classe durante il processo di <xref:Microsoft.VisualStudio.Package.ExpansionProvider> inserimento del frammento di codice:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Per altre informazioni su come ottenere un elenco di frammenti di codice installati per il servizio di linguaggio, vedere Procedura dettagliata: Recupero di un elenco di frammenti di codice installati [(implementazione legacy).](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

## <a name="implementing-the-expansionfunction-class"></a>Implementazione della classe ExpansionFunction
 Una funzione di espansione è una funzione denominata incorporata in un modello di frammento di codice e restituisce uno o più valori da inserire in un campo. Per supportare le funzioni di espansione nel servizio di linguaggio, è necessario derivare una classe dalla <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe e implementare il <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> metodo . È quindi necessario eseguire l'override del metodo nella classe per restituire una nuova istanza della versione della classe <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> per ogni funzione di espansione <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.ExpansionFunction> supportata. Se si supporta un elenco di valori possibili da una funzione di espansione, è anche necessario eseguire l'override del metodo nella classe per restituire <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> un elenco di tali <xref:Microsoft.VisualStudio.Package.ExpansionFunction> valori.

 Una funzione di espansione che accetta argomenti o deve accedere ad altri campi non deve essere associata a un campo modificabile, perché il provider di espansione potrebbe non essere completamente inizializzato al momento della chiamata della funzione di espansione. Di conseguenza, la funzione di espansione non è in grado di ottenere il valore degli argomenti o di qualsiasi altro campo.

### <a name="example"></a>Esempio
 Di seguito è riportato un esempio di come potrebbe essere implementata una `GetName` semplice funzione di espansione denominata . Questa funzione di espansione aggiunge un numero al nome di una classe di base ogni volta che viene creata un'istanza della funzione di espansione , che corrisponde a ogni inserimento del frammento di codice associato.

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
