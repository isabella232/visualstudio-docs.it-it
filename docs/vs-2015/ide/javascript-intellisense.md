---
title: IntelliSense per JavaScript |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 67
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 64da24c21ef40bd850e7fb91ed530df67bfe66b4
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54763284"
---
# <a name="javascript-intellisense"></a>IntelliSense per JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense consente di scrivere codice più velocemente e con meno errori fornendo informazioni durante la compilazione. Durante l’utilizzo di script client nell'editor JavaScript, in IntelliSense vengono elencati gli oggetti, le funzioni, le proprietà e i parametri disponibili in base al contesto corrente. È possibile selezionare un'opzione di codifica dall’elenco popup fornito da IntelliSense per completare il codice.

 IntelliSense semplifica il completamento delle seguenti attività:

- Trovare le informazioni su un membro.

- Inserire gli elementi del linguaggio direttamente nel codice.

- Gestire il contesto senza dover uscire dall’editor del codice.

- Supportare codice IntelliSense personalizzato con i commenti della documentazione XML e l'estensibilità JavaScript IntelliSense.

  Di seguito sono elencate le diverse sezioni di questo argomento:

- [Determinazione del contesto di IntelliSense](#DeterminingIntelliSenseContext)

- [Elaborazione delle informazioni di IntelliSense](#ProcessingIntelliSenseInformation)

- [Funzionalità di JavaScript IntelliSense](#Features)

- [Estensibilità JavaScript IntelliSense](#Extensibility)

- [Convalida JavaScript](#Validation)

  Per altre informazioni sulla funzionalità IntelliSense di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], vedere [Uso di IntelliSense](../ide/using-intellisense.md).

##  <a name="DeterminingIntelliSenseContext"></a> Determinazione del contesto di IntelliSense
 JavaScript IntelliSense consente di scegliere le opzioni di codifica in base all'intero script pertinente al contesto di script corrente. Ciò include gli elementi di scripting nel file corrente. Include anche qualsiasi codice al quale viene fatto direttamente o indirettamente riferimento dallo script, ad esempio riferimenti a file di script, riferimenti a script di assembly, riferimenti al servizio e riferimenti associati alla pagina.

 Il contesto di script corrente viene creato in base ai seguenti elementi:

-   Funzioni definite in qualsiasi blocco di script nel documento attivo. I blocchi di script online sono supportati in file con estensioni aspx., ascx, master, html e htm.

-   Elementi di`script` con attributi `src` che puntano a un altro file di script. Il file script di destinazione deve avere l'estensione js.

-   File JavaScript che fanno riferimento ad altri file dello stesso tipo utilizzando una direttiva `reference`.

-   Gruppi di riferimenti per oggetti globali, estensioni IntelliSense o file di script a caricamento ritardato.

-   Riferimenti a servizi Web XML.

-   Controlli <xref:System.Web.UI.ScriptManager> e <xref:System.Web.UI.ScriptManagerProxy>, se l'applicazione Web è un'applicazione ASP.NET abilitata per AJAX.

-   L' [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)], se si utilizza un'applicazione ASP.NET per AJAX.

    > [!NOTE]
    >  IntelliSense non è supportato per script incluso negli attributi del gestore eventi su elementi HTML, oppure definito negli attributi `href`.

##  <a name="ProcessingIntelliSenseInformation"></a> Elaborazione delle informazioni di IntelliSense
 Per fornire JavaScript IntelliSense, il servizio di linguaggio effettua le operazioni seguenti:

-   Crea un elenco di file JavaScript dipendenti basato sui riferimenti nel documento attivo e sui riferimenti allo script di analisi ricorsiva nei file di riferimento.

-   Analizza l'elenco e raccoglie informazioni sui tipi e altri dati rilevanti da ciascun file.

-   Aggrega i dati e li passa al motore del servizio di linguaggio JavaScript che rende disponibili in IntelliSense i dati e le informazioni sui tipi.

-   Controlla nei file le modifiche che potrebbero influire sull’elenco di IntelliSense e, se necessario, lo aggiorna. Gli script negli archivi remoti, ad esempio quelli a cui viene fatto riferimento tramite HTTP, non vengono monitorati.

##  <a name="Features"></a> Funzionalità di JavaScript IntelliSense
 JavaScript IntelliSense supporta gli oggetti indicati di seguito.

- [Elementi DOM (Document Object Model)](#HTMLDom)

- [Oggetti intrinseci](#IntrinsicObjects)

- [Variabili definite dall'utente, funzioni e oggetti](#UserDefined)

- Oggetti definiti in file esterni mediante riferimenti quali [riferimenti di script](#Script), [direttive reference](#ReferenceDirectives) e [gruppi di riferimenti](#ReferenceGroups).

- Oggetti definiti in file remoti scaricati da Visual Studio.

- Oggetti specificati nei [commenti della documentazione XML](#XMLDocComments), come parametri e campi.

- Oggetti descritti mediante tag di commento JavaScript standard (//). Per altre informazioni, vedere [Estensione di IntelliSense in JavaScript](../ide/extending-javascript-intellisense.md).

- Oggetti supportati mediante il [JavaScript IntelliSense estendibilità](#Extensibility) meccanismo. Per altre informazioni, vedere [Estensione di IntelliSense in JavaScript](../ide/extending-javascript-intellisense.md).

- [Oggetti AJAX ASP.NET](#ASPNet)

  Se IntelliSense non è in grado di determinare il tipo di un oggetto, fornisce opzioni per il completamento delle istruzioni utilizzando gli identificatori nel documento attivo. Per altre informazioni, vedere [completamento delle istruzioni per gli identificatori](../ide/statement-completion-for-identifiers.md).

###  <a name="HTMLDom"></a> Elementi DOM HTML
 JavaScript IntelliSense include riferimenti di programmazione per elementi DOM DHTML (Dynamic HTML), ad esempio `body`, `form` e `div`. Solo gli elementi inclusi nel documento corrente e la pagina master vengono visualizzati da IntelliSense. JavaScript IntelliSense supporta inoltre gli oggetti `window` e `document` e i relativi membri.

###  <a name="IntrinsicObjects"></a> Oggetti intrinseci
 JavaScript IntelliSense include riferimenti di programmazione per oggetti intrinseci, tra cui `Array`, `String`, `Math`, `Date` e `Number`. Per altre informazioni sugli oggetti intrinseci, vedere [Oggetti intrinseci](/visualstudio/scripting-docs/javascript/intrinsic-objects-javascript).

###  <a name="UserDefined"></a> Variabili definite dall'utente, funzioni e oggetti
 Quando si modifica un file JavaScript, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] analizza i documenti aperti e quelli a cui viene fatto riferimento per determinare tutte le risorse di codice disponibili, ad esempio le variabili, le funzioni e gli oggetti creati. Queste risorse diventano quindi disponibili per JavaScript IntelliSense.

 Per altre informazioni su variabili, funzioni e oggetti definiti dall'utente, vedere [Creazione di oggetti](http://go.microsoft.com/fwlink/?LinkId=108671) nel sito Web MSDN.

###  <a name="External"></a> Riferimenti a file esterni
 È possibile includere vari tipi di riferimenti a file esterni per ottenere il supporto IntelliSense nel codice. Può trattarsi di riferimenti di script, direttive reference oppure possono essere specificati mediante gruppi di riferimenti.

####  <a name="Script"></a> Riferimenti di script
 Anziché scrivere ogni script client in una pagina, è possibile fare riferimento a file esterni che includono codice di scripting. In questo modo è più facile riutilizzare il codice tra le pagine ed è possibile memorizzare lo script client nella cache del browser.

 Se non si utilizza una pagina Web ASP.NET per AJAX, è possibile fare riferimento a un file script esterno utilizzando l'attributo `src` nel tag di apertura di un elemento `script`. L'attributo `src` specifica l’URL a un file esterno che contiene il codice sorgente o i dati di origine.

 L'esempio seguente mostra il markup che usa l'attributo `src` in un tag <`script`> per fare riferimento a un file di script.

```html
<script type="text/javascript" src="~/Scripts/JavaScript.js">

</script>
```

 Se si utilizza una pagina Web ASP.NET per AJAX, è possibile fare riferimento ai file script utilizzando l'oggetto <xref:System.Web.UI.ScriptReference> del controllo <xref:System.Web.UI.ScriptManager>.

 Nell'esempio seguente è mostrato il markup che utilizza un oggetto <xref:System.Web.UI.ScriptReference> in un controllo <xref:System.Web.UI.ScriptManager> per fare riferimento a un file script.

```html
<asp:ScriptManager ID="ScriptManager1" runat="server">
  <Scripts>
    <asp:ScriptReference Path="~/Scripts/JavaScript.js" />
  </Scripts>
</asp:ScriptManager>
```

 IntelliSense supporta inoltre i file script incorporati come risorse in un assembly nelle applicazioni Web ASP.NET per AJAX. Per altre informazioni sulle risorse script incorporate, vedere [procedura dettagliata: incorporamento di un JavaScript File come risorsa in un Assembly](http://msdn.microsoft.com/library/d8cb78cd-95a9-4dc6-92df-391866817e89).

####  <a name="ReferenceDirectives"></a> Direttive reference
 Una direttiva `reference` consente a [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] di stabilire una relazione tra lo script in corso di modifica e gli altri script. La direttiva `reference` consente di includere un file script nel contesto di scripting del file script corrente in modo che sia possibile in IntelliSense fare riferimento a funzioni, tipi e campi definiti esternamente durante la compilazione.

 La direttiva `reference` viene creata nel form di un commento XML. La direttiva deve essere dichiarata prima nel file che in qualsiasi script. Una direttiva `reference` può includere un riferimento a script basato sul disco, un riferimento a script basato sull'assembly, un riferimento a script basato sul servizio o un riferimento a script basato sulla pagina.

 Nell'esempio seguente vengono mostrati alcuni utilizzi di direttive di riferimento basate su disco. Nel primo esempio, il servizio di linguaggio cerca il file nella stessa cartella che contiene il file di progetto, ad esempio .jsproj.

 `/// <reference path="ScriptFile1.js" />`

 `/// <reference path="Scripts/ScriptFile2.js" />`

 `/// <reference path="../ScriptFile3.js" />`

 `/// <reference path="~/Scripts/ScriptFile4.js" />`

 Nell'esempio seguente viene illustrato come creare un riferimento a uno script basato su assembly.

 `/// <reference name "Ajax.js" assembly="System.Web.Extensions, ..." />`

 Nell'esempio seguente viene illustrato come creare un riferimento a uno script basato su servizio.

 `/// <reference path="MyService.asmx" />`

 `/// <reference path="Services/MyService.asmx" />`

 `/// <reference path="../MyService.asmx" />`

 `/// <reference path="~/Services/MyService.asmx" />`

> [!NOTE]
>  JavaScript IntelliSense non è supportato per gli script contenuti nei file di servizi Web (.asmx) in WAP (Web Application Projects).

 Nell'esempio seguente viene illustrato come creare un riferimento a uno script basato su pagina.

 `/// <reference path="Default.aspx" />`

 `/// <reference path="Admin/Default.aspx" />`

 `/// <reference path="../Default.aspx" />`

 `/// <reference path="~/Admin/Default.aspx" />`

 Le seguenti regole si applicano a una direttiva `reference`.

-   Il commento XML `reference` deve essere dichiarato prima di qualsiasi script.

-   È necessario utilizzare sintassi di commenti XML con tre barre. I riferimenti creati utilizzando la sintassi dei commenti standard (due barre) vengono ignorati.

-   È possibile specificare solo un file o una risorsa per direttiva.

-   Non sono consentiti più riferimenti a script basati su pagina.

-   Se viene specificato un riferimento alla pagina, non sono consentiti altri tipi di direttive di riferimento.

-   I nomi di file utilizzano percorsi relativi. È possibile usare l'operatore tilde (`~`) per creare percorsi relativi alla directory radice dell'applicazione.

-   I percorsi assoluti vengono ignorati.

-   Le direttive di riferimento nelle pagine a cui si fa riferimento non verranno elaborate, ciò significa che le direttive di riferimento non vengono risolte in modo ricorsivo per le pagine. È incluso solo script al quale viene fatto riferimento direttamente dalla pagina.

####  <a name="ReferenceGroups"></a> Gruppi di riferimenti
 È possibile utilizzare gruppi di riferimenti predefiniti per specificare che determinati file .js IntelliSense rientrino nell'ambito per progetti JavaScript diversi. Sono disponibili i tipi di gruppi di riferimenti indicati di seguito.

- Implicito (Windows), per le app [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] che utilizzano JavaScript. I file inclusi in questo gruppo rientrano nell'ambito per ogni file .js aperto nell'editor di codice per il progetto del tipo specificato.

- Implicito (Web), per progetti HTML5. I file inclusi in questo gruppo rientrano nell'ambito per ogni file .js aperto nell'editor di codice per questi tipi di progetto.

- Gruppi di riferimenti a processi di lavoro dedicati, per lavori Web HTML5. I file specificati in questo gruppo rientrano nell'ambito per i file .js con un riferimento esplicito a un gruppo di riferimenti a processi di lavoro dedicati.

- Generico, per altri tipi di progetti JavaScript.

  Nella maggior parte degli scenari, non è necessario modificare i gruppi di riferimenti. Se tuttavia si desidera apportare modifiche, è possibile utilizzare le opzioni di configurazione dell'editor di codice JavaScript per specificare i file inclusi nei gruppi di riferimenti. Per istruzioni su come usare questa funzionalità, vedere [Opzioni, Editor di testo, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

> [!TIP]
>  I riferimenti di IntelliSense vengono in genere utilizzati per fornire il supporto IntelliSense per oggetti globali ed [estensioni](#Extensibility) IntelliSense. È inoltre possibile utilizzare questa funzionalità per gli script che devono essere caricati al runtime utilizzando il caricatore di script.

### <a name="remote-file-references"></a>Riferimenti a file remoti
 È possibile configurare Visual Studio in modo che scarichi i file JavaScript remoti a cui viene fatto riferimento in un file JavaScript per fornire il supporto IntelliSense per la libreria o il file remoto. Se si utilizza questa funzionalità, i file verranno scaricati nel momento in cui verranno inclusi come riferimento nel file JavaScript.

> [!NOTE]
>  Ad eccezione dei progetti Web, questa funzionalità si applica solo ai file JavaScript aperti all'esterno del contesto di un progetto. Per i progetti Web, i file remoti a cui viene fatto riferimento nel progetto vengono scaricati per impostazione predefinita.

 Per istruzioni su come usare questa funzionalità, vedere [Opzioni, Editor di testo, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

> [!WARNING]
>  Se si abilita questa funzionalità e si verifica un rallentamento delle prestazioni dell'editor del codice, è consigliabile disabilitarla.

###  <a name="XMLDocComments"></a> Commenti relativi alla documentazione XML
 I commenti della documentazione XML sono descrizioni di testo di elementi di codice che si aggiungono agli script. Queste descrizioni di testo vengono visualizzate in IntelliSense quando si fa riferimento allo script commentato. Ad esempio, è possibile fornire informazioni sui parametri e sul valore restituito di una funzione. I commenti della documentazione XML sono disponibili solo dai file, dagli assembly e dai servizi di riferimento. Per altre informazioni, vedere [commenti in formato documentazione XML](../ide/xml-documentation-comments-javascript.md) e [creare commenti in formato documentazione XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

 IntelliSense può visualizzare i commenti della documentazione XML negli scenari indicati di seguito.

- Un file JS che fa riferimento a un altro file JS.

- Un file JS che fa riferimento a un file ASPX.

- Un file ASPX che fa riferimento a un file JS.

  IntelliSense non è disponibile quando uno file ASPX fa riferimento a un altro file ASPX.

###  <a name="ASPNet"></a> Oggetti AJAX ASP.NET
 JavaScript IntelliSense è supportato anche in ASP.NET per AJAX. ASP.NET AJAX include un framework client che estende i tipi standard disponibili in ECMAScript (JavaScript). Per consentire a JavaScript IntelliSense di fornire dettagli sugli oggetti ASP.NET per AJAX, i commenti della documentazione XML sono stati aggiunti mediante [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)]. Questi commenti della documentazione XML vengono visualizzati quando si utilizzano tipi e membri contenuti nella libreria ASP.NET AJAX.

> [!NOTE]
>  I membri privati non vengono visualizzati da JavaScript IntelliSense. e ASP.NET per AJAX vengono indicati come membri che iniziano con un carattere di sottolineatura (_).

##  <a name="Extensibility"></a> Estensibilità JavaScript IntelliSense
 JavaScript Language Service fornisce oggetti e funzioni che consentono di modificare l'esperienza IntelliSense per gli sviluppatori che utilizzano librerie di terze parti. Queste funzionalità risultano particolarmente utili se il servizio di linguaggio predefinito non riesce a fornire tutte le informazioni desiderate per i clienti. Per altre informazioni, vedere [Estensione di IntelliSense in JavaScript](../ide/extending-javascript-intellisense.md).

##  <a name="Validation"></a> Convalida JavaScript
 La convalida di scripting JavaScript si verifica costantemente in background. Se [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rileva errori di sintassi nel codice JavaScript, viene fornito un feedback nelle modalità indicate di seguito.

-   Elementi sottolineati nell'editor. Sottolineature rosse ondulate indicano errori. Se si mantiene il puntatore del mouse sull'errore, verrà visualizzata la descrizione dell’errore.

-   Finestra **Elenco errori**. La finestra **Elenco errori** mostra la descrizione dell'errore, il file in cui si verifica, la riga e il numero di colonna e il progetto. Per visualizzare la finestra **Elenco errori**, scegliere **Elenco errori** dal menu **Visualizza**.

-   Nella finestra di output vengono visualizzati i riferimenti non caricati.

## <a name="see-also"></a>Vedere anche
- [Utilizzo di IntelliSense](../ide/using-intellisense.md)
- [Creare commenti relativi alla documentazione XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)
- [Estensione di IntelliSense in JavaScript](../ide/extending-javascript-intellisense.md)
- [Completamento delle istruzioni per gli identificativi](../ide/statement-completion-for-identifiers.md)
- [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)
- [Informazioni sul modello a oggetti DHTML](http://go.microsoft.com/fwlink/?LinkID=92344)
- [Elenca membri](http://msdn.microsoft.com/1b9cc469-9cd4-4d42-9999-1f9479635ff8)
- [Attributo SRC di &#124; proprietà src](http://go.microsoft.com/fwlink/?LinkId=92345)