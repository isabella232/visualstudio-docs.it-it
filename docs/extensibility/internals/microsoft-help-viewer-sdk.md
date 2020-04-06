---
title: SDK del Visualizzatore della Guida Di Microsoft Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 721623edabcaf3b395a143dd193cae3fd71d93d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707145"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK

In questo articolo contiene le attività seguenti per gli integratori del Visualizzatore della Guida di Visual Studio:

- Creazione di un argomento (supporto F1)

- Creazione di un pacchetto di personalizzazione del contenuto del Visualizzatore della Guida

- Distribuzione di un set di articoliDeploying a set of articles

- Aggiunta della Guida alla shell di Visual Studio (integrata o isolata)

- Risorse aggiuntive

## <a name="create-a-topic-f1-support"></a>Creare un argomento (supporto F1)

In questa sezione viene fornita una panoramica dei componenti di un argomento presentato, dei requisiti degli argomenti, una breve descrizione della creazione di un argomento (inclusi i requisiti di supporto F1) e infine un argomento di esempio con il relativo risultato sottoposto a rendering.

**Panoramica dell'argomento del Visualizzatore della Guida**

Quando un argomento viene chiamato per il rendering, il visualizzatore della Guida ottiene gli elementi del pacchetto di personalizzazione associati all'argomento al momento dell'installazione o dell'ultimo aggiornamento, insieme all'argomento XHTML, e combina i due per ottenere la visualizzazione del contenuto presentato (dati di personalizzazione e dati dell'argomento).  Il pacchetto di personalizzazione contiene loghi, supporto per i comportamenti dei contenuti e testo di personalizzazione (copyright, ecc.).  Vedere "Creazione di un pacchetto di personalizzazione" di seguito per ulteriori informazioni sugli elementi del pacchetto di personalizzazione.  Nel caso in cui all'argomento non sia associato alcun pacchetto di personalizzazione, il visualizzatore della Guida utilizzerà il pacchetto di personalizzazione di fallback disponibile nella radice dell'applicazione del Visualizzatore della Guida (Branding_en-US.mshc).

**Requisiti degli argomenti del Visualizzatore della Guida**

Per eseguire correttamente il rendering all'interno del Visualizzatore della Guida, il contenuto dell'argomento non elaborato deve essere W3C Basic 1.1 XHTML.

Un argomento contiene in genere due sezioni:A topic typically contains two sections:

- Metadati (vedere Riferimento ai metadati del contenuto): dati relativi all'argomento, ad esempio l'ID univoco dell'argomento, il valore della parola chiave, l'ID del sommario dell'argomento, l'ID del nodo padre e così via.

- Contenuto del corpo: compatibile con W3C Basic 1.1 XHTML, che include comportamenti di contenuto supportati (area comprimibile, frammento di codice e così via). Di seguito è riportato un elenco completo).

Controlli supportati dal pacchetto di personalizzazione di Visual Studio:Visual Studio Branding Package supported controls:

- Collegamenti

- CodeSnippet

- CollapsibleArea

- Membro ereditato

- TestoSpecifico

Stringhe di lingua supportate (senza distinzione tra maiuscole e minuscole):Supported language strings (not case sensitive):

- JavaScript

- csharp o csharp o c #

- cplusplus o visualc o c

- jscript

- visualbasic o vb

- f o fsharp o fs

- other - una stringa che rappresenta un nome di lingua

**Creazione di un argomento del Visualizzatore della Guida**

Creare un nuovo documento XHTML denominato ContosoTopic4.htm e includere il tag title (sotto).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Aggiungere quindi i dati per definire come deve essere presentato l'argomento (automarcato o meno), come fare riferimento a questo argomento per F1, dove questo argomento è presente all'interno del sommario, il relativo ID (per riferimento ai collegamenti da altri argomenti) e così via. Vedere la tabella "Metadati del contenuto" di seguito per un elenco completo dei metadati supportati.

- In questo caso, useremo il nostro pacchetto di personalizzazione, una variante del pacchetto di personalizzazione del Visualizzatore della Guida di Visual Studio.

- Aggiungere il nome meta F1 e il valore ("Microsoft.Help.F1" content : " ContosoTopic4") che corrisponderà al valore F1 fornito nel contenitore delle proprietà dell'IDE. Per ulteriori informazioni, vedere la sezione Supporto F1. Questo è il valore che corrisponde alla chiamata F1 dall'interno dell'IDE per visualizzare questo argomento quando si presta F1 nell'IDE.

- Aggiungere l'ID dell'argomento. Si tratta della stringa utilizzata da altri argomenti per il collegamento a questo argomento. Si tratta dell'ID visualizzatore della Guida per questo argomento.

- Per il sommario, aggiungere il nodo padre di questo argomento per definire la posizione in cui verrà visualizzato il nodo del sommario dell'argomento.

- Per il sommario, aggiungere l'ordine dei nodi di questo argomento. Quando il nodo `n` padre ha un numero di nodi figlio, definire nell'ordine dei nodi figlio la posizione di questo argomento. Ad esempio, questo argomento è il numero 4 di 4 argomenti figlio.

Sezione dei metadati di esempio:Example metadata section:

```html
<html>
<head>
<title>Contoso Topic 4</title>

<meta name="SelfBranded" content="false" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />

</head>

<body>

</body>
</html>
```

**Il corpo dell'argomento**

Il corpo (esclusi l'intestazione e il piè di pagina) dell'argomento conterrà collegamenti a pagine, una sezione di note, un'area comprimibile, uno snippet di codice e una sezione di testo specifico della lingua.  Vedere la sezione di branding per informazioni sulle aree dell'argomento presentato.

1. Aggiungere un tag titolo argomento:`<div class="title">Contoso Topic 4</div>`

2. Aggiungere una sezione nota:`<div class="alert"> add your table tag and text </div>`

3. Aggiungere un'area comprimibile:`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Aggiungere uno snippet di codice:Add a code snippet:`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Aggiungere testo specifico della `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` lingua `devLangnu=` del codice: si noti che consente di immettere altre lingue. Ad esempio, `devLangnu="Fortran"` visualizza Fortran quando il frammento di codice DisplayLanguage

6. Aggiungere collegamenti a pagine:`<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Nota: per la nuova "Lingua di visualizzazione" non supportata (ad esempio, F , Cobol, Fortran) colorazione del codice nel frammento di codice sarà monocromatica.

**Esempio di argomento del Visualizzatore della Guida** Il codice illustra come definire i metadati, un frammento di codice, un'area comprimibile e testo specifico della lingua.

```html
<?xml version="1.0" encoding="utf-8"?>
<html>
<head>
<title>Contoso Topic 4</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />
<meta name="SelfBranded" content="false" />
</head>

<body>
<div class="title">Contoso Topic 4</div>

  <div id="header">
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">
        <tr id="headerTableRow2"><td align="left">
            <span id="nsrTitle">Contoso Topic 1</span>
          </td>
<td align="right">
</td></tr>
<tr id="headerTableRow1"><td align="left">
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>
          </td></tr>
      </table>
</div>

<h2>Table of Contents</h2>

<ul class="toc">
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>
</ul>

<div class="topic">

<div id="mainSection">
<div id="mainBody">

<a name="introduction"></a>
<h2>1.0 Introduction</h2>
<p>[This documentation is for sample purposes only.]</p>

<p>Contoso Topic 1 contains examples of:
<ul>
<li>Collapsible Area</li>
<li>Bookmark ("See also")</li>
<li>Code Snippets from Branding Package</li>
</ul>
 </p>
<div class="alert"><table><tr><th>
<strong>Note </strong></th></tr>
<tr><td>
<p>This is an example of a <span class="label">Note </span>section.
Call out important items for your reader in this <span class="label">Note </span>box.
</p></td></tr>
</table>
</div>
</div>

<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">

            <a id="sectionToggle0"><!----></a>

<div>
Example of Collapsible Area
<br/>
Lorem ipsum dolor sit amet...
</div>
</CollapsibleArea>

<div id="snippetGroup" >
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip
Dim messageBoxVB as New System.Text.StringBuilder()
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)
    messageBoxVB.AppendLine()
 ...
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")
End Sub
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)
{
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );
messageBoxCS.AppendLine();
...
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );
}
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >
some F# code
</CodeSnippet>
</div>

<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />

<a name="seealso"></a>
<h1 class="heading">See Also</h1>

    <div id="seeAlsoSection" class="section">
    <div class="seeAlsoStyle">
        <a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**Supporto F1**

In Visual Studio, selezionando F1 vengono generati i valori forniti dalla posizione del cursore all'interno dell'IDE e viene popolato un "contenitore delle proprietà" con i valori forniti (in base alla posizione del cursore. Quando il cursore è posizionato sulla feature x, la feature x è attiva/in stato attivo e popola il contenitore delle proprietà con i valori.  Quando si seleziona F1 il contenitore delle proprietà viene popolato e il codice Visual Studio F1 cerca se l'origine della Guida predefinita dei clienti è locale o online (online è l'impostazione predefinita), quindi crea la stringa appropriata in base all'impostazione degli utenti (online è l'impostazione predefinita) - shell execute (vedere la Guida dell'amministratore per i parametri di avvio exe) con i parametri per le parole chiave del visualizzatore della Guida locale , ovvero le parole chiave del visualizzatore della Guida locale, se la Guida locale è l'impostazione predefinita o l'URL MSDN con la parola chiave nell'elenco di parametri.

Se vengono restituite tre stringhe per F1, definito stringa multivalore, prendere il primo termine, cercare un hit e, se trovato, abbiamo finito; in caso contrario, passare alla stringa successiva.  L'ordine è importante. La presentazione delle parole chiave multivalore deve essere una stringa più lunga alla stringa più breve.  Per verificarlo nel caso di parole chiave multivalore, esaminare la stringa dell'URL F1 online, che includerà la parola chiave scelta.

In Visual Studio 2012, abbiamo intenzionalmente fatto una divisione più forte tra online e offline, in modo che se l'impostazione dell'utente era per Online, quindi abbiamo semplicemente passato la richiesta F1 direttamente al nostro servizio di query online su MSDN piuttosto che il routing attraverso l'agente della libreria di Guida che avevamo in Visual Studio 2010. Ci affidiamo quindi a uno stato di "contenuto del fornitore installato - true" per determinare se fare qualcosa di diverso in quel contesto. Se true, eseguiamo questa logica di analisi e routing a seconda di ciò che si desidera supportare per i clienti. Se false, allora basta andare a MSDN. Se l'impostazione dell'utente è Locale, tutte le chiamate vengono richiamate al motore della Guida locale.

Diagramma di flusso F1:

![Flusso F1](../../extensibility/internals/media/f1flow.png "Flusso F1")

Quando l'origine di contenuto della Guida predefinita del Visualizzatore della Guida è impostata su online (Avvia nel browser):

- Le funzionalità di Visual Studio Partner (VSP) generano un valore per il contenitore delle proprietà F1 (prefisso del contenitore delle proprietà.parola chiave e URL online per il prefisso trovato nel Registro di sistema): F1 invia un URL VSP parametri al browser.

- Funzionalità di Visual Studio (editor di linguaggio, voci di menu specifiche di Visual Studio e così via): F1 invia un URL di Visual Studio al browser.

Quando l'origine di contenuto predefinito della Guida del Visualizzatore della Guida è impostata sulla Guida locale (Avvia nel Visualizzatore della Guida):

- Funzionalità VSP in cui la corrispondenza delle parole chiave tra il contenitore delle proprietà F1 e l'indice dell'archivio locale (vale a dire, il prefisso del contenitore delle proprietà.parola chiave- il valore trovato nell'indice dell'archivio locale): F1 esegue il rendering dell'argomento nel Visualizzatore della Guida.

- Funzionalità di Visual Studio (nessuna opzione per il VSP per eseguire l'override del contenitore delle proprietà generato dalle funzionalità di Visual Studio): F1 esegue il rendering di un argomento di Visual Studio nel Visualizzatore della Guida.

Impostare i seguenti valori del Registro di sistema per abilitare il fallback F1 per il contenuto della Guida fornitore. F1 Fallback significa che il visualizzatore della Guida è impostato per cercare il contenuto della Guida F1 online e il contenuto del fornitore viene installato localmente sul disco rigido degli utenti. Il visualizzatore della Guida deve esaminare la Guida locale per il contenuto anche se l'impostazione predefinita è per la Guida in linea.

1. Impostare il valore **VendorContent** nella chiave del Registro di sistema Help 2.3:

   - Per i sistemi operativi a 32 bit:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "ContenutoFornitore" - dword:00000001

   - Per i sistemi operativi a 64 bit:

        HKEY_LOCAL_MACHINE software: Wow6432Node, Microsoft . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

        "ContenutoFornitore" - dword:00000001

2. Registrare lo spazio dei nomi del partner nella chiave del Registro di sistema Help 2.3:

   - Per i sistemi operativi a 32 bit:

      spazio dei nomi<del partner<em> \\ HKEY_LOCAL_MACHINE SOFTWARE\></em>

      "posizione"-" offline"

   - Per i sistemi operativi a 64 bit:

      spazio dei nomi<em> \\<HKEY_LOCAL_MACHINE\></em>

      "posizione"-" offline"

**Analisi dello spazio dei nomi nativo di baseBase Native Namespace Parsing**

Per attivare l'analisi dello spazio dei nomi nativo di base, nel Registro di sistema aggiungere un nuovo DWORD con il nome di: BaseNativeNamespaces e impostarne il valore su 1 (nella chiave di catalogo che si desidera supportare).  Ad esempio, se si desidera utilizzare il catalogo di Visual Studio, è possibile aggiungere la chiave al percorso:For example, if you want to use the Visual Studio catalog, you could add the key to the path:

HKEY_LOCAL_MACHINE software: Wow6432Node, Microsoft . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

Quando viene rilevata una parola chiave F1 nel formato HEADER/METHOD, il carattere '/' verrà analizzato, generando il seguente costrutto:

- HEADER: sarà lo spazio dei nomi che può essere utilizzato per la registrazione nel Registro di sistema

- METODO: questa diventerà la parola chiave che viene passata attraverso.

Ad esempio, data una libreria personalizzata denominata CustomLibrary e un metodo denominato MyTestMethod, quando arriva una richiesta F1 verrà formattato come `CustomLibrary/MyTestMethod`.

Un utente può quindi registrare CustomLibrary come spazio dei nomi nell'hive Partners e fornire la chiave di posizione desiderata e la parola chiave passata alla query sarà MyTestMethod.

**Abilitare lo strumento di debug della Guida nell'IDEEnable Help debugging tool in the IDE**

Aggiungere la seguente chiave del Registro di sistema e il valore:

::: moniker range="vs-2017"

**HKEY_CURRENT_USER software Microsoft Microsoft VisualStudio 15.0 - Guida dinamica**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER software Microsoft Visual Studio 16.0 - Guida dinamica**

::: moniker-end

Valore: Visualizza output di debug nei dati di vendita al dettaglio: YES

Nell'IDE, nella voce di menu Guida, selezionare **Debug ambito della Guida**.

**Metadati del contenuto**

Nella tabella seguente, qualsiasi stringa visualizzata tra parentesi quadre è un segnaposto che deve essere sostituito da un valore riconosciuto. Ad esempio, \<in meta name, "Microsoft.Help.Locale" content "[codice lingua]" />, "[codice lingua]" deve essere sostituito da un valore quale "en-us".

| Proprietà (rappresentazione HTML) | Descrizione |
| - | - |
| \<meta name: "Microsoft.Help.Locale" content "[codice lingua]" /> | Imposta le impostazioni locali per questo argomento. Se questo tag viene utilizzato in un argomento, deve essere utilizzato una sola volta e deve essere inserito sopra qualsiasi altro tag della Guida Microsoft. Se questo tag non viene utilizzato, il testo del corpo dell'argomento viene indicizzato utilizzando il word breaker associato alle impostazioni locali del prodotto, se specificato; in caso contrario, viene utilizzato il word breaker en-us. Questo tag è conforme a ISOC RFC 4646. Per assicurarsi che la Guida Microsoft funzioni correttamente, utilizzare questa proprietà anziché l'attributo generale Language. |
| \<meta name: "Microsoft.Help.TopicLocale" content "[codice lingua]" /> | Imposta le impostazioni locali per questo argomento quando vengono utilizzate anche altre impostazioni locali. Se questo tag viene utilizzato in un argomento, deve essere utilizzato una sola volta. Utilizzare questo tag quando il catalogo include contenuto in più lingue. Più argomenti in un catalogo possono avere lo stesso ID, ma ognuno deve specificare un TopicLocale univoco. L'argomento che specifica un TopicLocale che corrisponde alle impostazioni locali del catalogo è l'argomento visualizzato nel sommario. Tuttavia, tutte le versioni linguistiche dell'argomento vengono visualizzate nei risultati della ricerca. |
| \<title>[Titolo]\</title> | Specifica il titolo di questo argomento. Questo tag è obbligatorio e deve essere utilizzato una sola volta in un argomento. Se il corpo dell'argomento non \<contiene un titolo div> sezione, questo titolo viene visualizzato nell'argomento e nel sommario. |
| \<meta name "Microsoft.Help.Keywords" content"[aKeywordPhrase]"/> | Specifica il testo di un collegamento visualizzato nel riquadro dell'indice del Visualizzatore della Guida. Quando si fa clic sul collegamento, viene visualizzato l'argomento. È possibile specificare più parole chiave di indice per un argomento oppure omettere questo tag se non si desidera che i collegamenti a questo argomento vengano visualizzati nell'indice. Le parole chiave "K" delle versioni precedenti della Guida possono essere convertite in questa proprietà. |
| \<meta name: "Microsoft.Help.Id" content "[TopicID]"/> | Imposta l'identificatore per questo argomento. Questo tag è obbligatorio e deve essere utilizzato una sola volta in un argomento. L'ID deve essere univoco tra gli argomenti del catalogo con le stesse impostazioni locali. In un altro argomento, è possibile creare un collegamento a questo argomento utilizzando questo ID. |
| \<meta name: "Microsoft.Help.F1" content"[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Specifica la parola chiave F1 per questo argomento. È possibile specificare più parole chiave F1 per un argomento oppure omettere questo tag se non si desidera che questo argomento venga visualizzato quando un utente dell'applicazione preme F1. In genere, per un argomento viene specificata una sola parola chiave F1. Le parole chiave "F" delle versioni precedenti della Guida possono essere convertite in questa proprietà. |
| \<meta name: "Descrizione" content"[descrizione argomento]" /> | Fornisce un breve riepilogo del contenuto di questo argomento. Se questo tag viene utilizzato in un argomento, deve essere utilizzato una sola volta. Questa proprietà è accessibile direttamente dalla libreria di query; non è memorizzato nel file di indice. |
| meta name: "Microsoft.Help.TocParent" content "[parent_Id]"/> | Specifica l'argomento padre di questo argomento nel sommario. Questo tag è obbligatorio e deve essere utilizzato una sola volta in un argomento. Il valore è il Microsoft.Help.Id dell'elemento padre. Un argomento può avere una sola posizione nel sommario. "-1" è considerato l'ID dell'argomento per la radice del sommario. In [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], tale pagina è la home page del Visualizzatore della Guida. Questo è lo stesso motivo per cui aggiungiamo specificamente TocParent-1 ad alcuni argomenti per garantire che vengano visualizzati al livello superiore. La home page del Visualizzatore della Guida è una pagina di sistema e quindi non sostituibile. Se un VSP tenta di aggiungere una pagina con ID -1, è possibile che venga aggiunta al set di contenuti, ma il visualizzatore della Guida utilizzerà sempre la pagina di sistema - Home page del visualizzatore della Guida |
| \<meta name: "Microsoft.Help.TocOrder" content "[positive integer]"/> | Specifica la posizione nel sommario di questo argomento rispetto agli argomenti peer. Questo tag è obbligatorio e deve essere utilizzato una sola volta in un argomento. Il valore è un numero intero. Un argomento che specifica un numero intero di valore inferiore viene visualizzato sopra un argomento che specifica un numero intero di valore superiore. |
| \<meta name: "Microsoft.Help.Product" content "[codice prodotto]"/> | Specifica il prodotto descritto in questo argomento. Se questo tag viene utilizzato in un argomento, deve essere utilizzato una sola volta. Queste informazioni possono essere fornite anche come parametro che viene passato all'indicizzatore della Guida. |
| \<meta name: "Microsoft.Help.ProductVersion" content "[numero di versione]"/> | Specifica la versione del prodotto descritta in questo argomento. Se questo tag viene utilizzato in un argomento, deve essere utilizzato una sola volta. Queste informazioni possono essere fornite anche come parametro che viene passato all'indicizzatore della Guida. |
| \<meta name: "Microsoft.Help.Category" content "[stringa]"/> | Utilizzato dai prodotti per identificare sottosezioni di contenuto. È possibile identificare più sottosezioni per un argomento oppure omettere questo tag se non si desidera che i collegamenti identifichino le sottosezioni. Questo tag viene utilizzato per archiviare gli attributi per TargetOS e TargetFrameworkMoniker quando un argomento viene convertito da una versione precedente della Guida. Il formato del contenuto è AttributeName:AttributeValue. |
| \<meta name: "Microsoft.Help.TopicVersion content"[numero di versione dell'argomento]"/> | Specifica questa versione dell'argomento quando in un catalogo sono presenti più versioni. Poiché non è garantito che Microsoft.Help.Id sia univoco, questo tag è necessario quando in un catalogo sono presenti più versioni di un argomento, ad esempio quando un catalogo contiene un argomento per .NET Framework 3.5 e un argomento per .NET Framework 4 ed entrambi hanno lo stesso Microsoft.Help.Id. |
| \<meta name: "SelfBranded" content "[TRUE o FALSE]"/> | Specifica se in questo argomento viene utilizzato il pacchetto di personalizzazione di avvio di Gestione librerie della Guida o un pacchetto di personalizzazione specifico dell'argomento. Questo tag deve essere TRUE o FALSE. Se è TRUE, il pacchetto di personalizzazione per l'argomento associato esegue l'override del pacchetto di personalizzazione impostato all'avvio di Gestione librerie della Guida in modo che il rendering dell'argomento venga eseguito come previsto anche se è diverso dal rendering di altro contenuto. Se è FALSE, il rendering dell'argomento corrente viene eseguito in base al pacchetto di personalizzazione impostato all'avvio di Gestione librerie della Guida. Per impostazione predefinita, Gestione librerie della Guida presuppone che la codifica autonoma sia false, a meno che la variabile SelfBranded non sia dichiarata TRUE; pertanto, non è \<necessario dichiarare il nome del meta "SelfBranded" content "FALSE" />. |

## <a name="create-a-branding-package"></a>Creare un pacchetto di personalizzazioneCreate a branding package

La versione di Visual Studio comprende una serie di diversi prodotti di Visual Studio, tra cui le shell isolate e integrate per i partner di Visual Studio.  Ognuno di questi prodotti richiede un certo grado di supporto per la personalizzazione del contenuto della Guida basato su argomenti, univoco per il prodotto.  Ad esempio, gli argomenti di Visual Studio devono avere una presentazione coerente del marchio, mentre SQL Studio, che esegue il wrapping di ISO Shell, richiede la personalizzazione del contenuto della Guida univoco per ogni argomento.  Un partner della shell integrata potrebbe richiedere che i relativi argomenti della Guida si risiedano all'interno del contenuto della Guida del prodotto Visual Studio padre, mantenendo il proprio personalizzazione dell'argomento.

I pacchetti di personalizzazione vengono installati dal prodotto contenente il visualizzatore della Guida.  Per i prodotti Visual Studio:

- Un pacchetto di\<personalizzazione di fallback (Branding_ impostazioni locali>.mshc) viene installato nella radice dell'app del Visualizzatore della Guida 2.3 (ad esempio: C:.  Viene utilizzato per i casi in cui il pacchetto di personalizzazione del prodotto non è installato (non è stato installato alcun contenuto) o in cui il pacchetto di personalizzazione installato è danneggiato.  Gli elementi di Visual Studio (logo e feedback) vengono ignorati quando viene usato il pacchetto di personalizzazione del fallback radice dell'app.

- Quando il contenuto di Visual Studio viene installato dal servizio del pacchetto di contenuto, viene installato anche un pacchetto di personalizzazione (per il primo scenario di installazione del contenuto).  Se è presente un aggiornamento al pacchetto di personalizzazione, l'aggiornamento viene installato quando si verifica il successivo aggiornamento del contenuto o l'azione di installazione del pacchetto aggiuntivo.

Il Visualizzatore della Guida Microsoft supporta la personalizzazione degli argomenti in base ai metadati dell'argomento.

- Dove i metadati dell'argomento definiscono self-branded - true, eseguire il rendering dell'argomento così com'è, non eseguire alcuna operazione (per quanto riguarda il branding).

- In cui i metadati dell'argomento definiscono self-branded, ovvero false, usa il pacchetto di personalizzazione associato al valore dei metadati TopicVendor.

- Se i metadati dell'argomento definiscono il nome\< del pacchetto di personalizzazione name"Microsoft.Help.TopicVendor" nel> MSHA del fornitore, utilizzare il pacchetto di personalizzazione definito nel valore del contenuto.

- All'interno del catalogo di Visual Studio, è disponibile un'applicazione prioritaria di pacchetti di personalizzazione.  Viene applicata innanzitutto la personalizzazione predefinita di Visual Studio e quindi, se definita nei metadati dell'argomento e supportata con il pacchetto di personalizzazione associato (come definito nell'msha di installazione), la personalizzazione definita dal fornitore viene applicata come override.

Gli elementi di personalizzazione in genere rientrano in tre categorie principali:

- Elementi di intestazione (gli esempi includono il collegamento di feedback, il testo della dichiarazione di non responsabilità condizionale, il logo)

- Comportamenti del contenuto (gli esempi includono gli elementi di testo del controllo di espansione/compressione ed elementi di frammenti di codice)Content behaviors (examples include expand/collapse control control text elements and code snippet elements)

- Elementi del piè di pagina (esempio Copyright)

Gli elementi considerati come elementi di marca includono (dettagliato in questa specifica):

- Logo catalogo/prodotto (esempio, Visual Studio)

- Collegamento di feedback ed elementi di posta elettronica

- Testo della dichiarazione di non responsabilità

- Testo di copyright

I file di supporto nel pacchetto di personalizzazione del Visualizzatore della Guida di Visual Studio includono:Supporting files in the Visual Studio Help Viewer branding package include:

- Grafica (logo, icone, ecc.)

- Branding.js - file di script che supportano i comportamenti del contenuto

- Branding.xml: stringhe utilizzate in modo coerente nel contenuto del catalogo.  Nota: per gli elementi di testo di localizzazione\<di Visual Studio nel file branding.xml, includere _locID valore univoco>"

- Branding.css - definizioni di stile per la coerenza della presentazione

- Printing.css - definizioni di stile per una presentazione stampata coerente

Come indicato in precedenza, i pacchetti di personalizzazione sono associati all'argomento:

- Quando nei metadati è definito SelfBranded - false, l'argomento eredita il pacchetto di personalizzazione del catalogo

- Oppure, quando SelfBranded è false ed è presente un pacchetto di personalizzazione univoco definito in MSHA e disponibile quando il contenuto viene installato

Per i servizi VSP che implementano pacchetti di personalizzazione personalizzati (contenuto VSP, SelfBranded -True), un modo per procedere consiste nell'iniziare con il pacchetto di personalizzazione di fallback (installato con il Visualizzatore della Guida) e modificare il nome del file in base alle esigenze.  Il\<file>.mshc delle impostazioni locali Branding_ è un file zip con l'estensione del file modificata in .mshc, quindi è sufficiente modificare l'estensione da .mshc a .zip ed estrarre il contenuto.  Vedere di seguito per gli elementi del pacchetto di personalizzazione e modificarli in base alle esigenze (ad esempio, modificare il logo nel logo VSP e il riferimento al logo nel file Branding.xml, aggiornare Branding.xml per le specifiche VSP e così via).

Al termine di tutte le modifiche, creare un file zip contenente gli elementi di personalizzazione desiderati e modificare l'estensione in .mshc.

Per associare il pacchetto di personalizzazione, creare il msHA, che contiene il riferimento al file mshc di personalizzazione insieme al contenuto mshc (contenente gli argomenti).  Vedere di seguito "MSHA" per informazioni su come creare un MSHA di base.

Il file Branding.xml contiene un elenco di elementi utilizzati per \<il rendering coerente di elementi specifici in un argomento quando l'argomento contiene meta name , "Microsoft.Help.SelfBranded" content , "false"/>.  L'elenco di elementi di Visual Studio nel file Branding.xml è elencato di seguito.  Questo elenco deve essere utilizzato come modello per gli utenti di ISO Shell, in cui modificano questi elementi (ad esempio logo, feedback e copyright) per soddisfare le proprie esigenze di branding del prodotto.

Nota: le variabili annotate da "n" hanno dipendenze del codice: la rimozione o la modifica di questi valori causerà errori ed eventualmente l'arresto anomalo dell'applicazione. Gli identificatori di localizzazione (ad esempio _locID"codesnippet.n") sono inclusi nel pacchetto di personalizzazione di Visual Studio.Localization identifiers (example _locID'"codesnippet.n") are included in the Visual Studio Branding Package.

**Branding.xml**

| | |
| - | - |
| Funzionalità: | **CollapsibleArea** |
| Usare: | Espandi comprime il testo del controllo contenuto |
| **Elemento** | **valore** |
| TestoSpanta | Espandere |
| CollapseText (Testo)CollapseText ( | Comprimi |
| Funzionalità: | **CodeSnippet** |
| Usare: | Testo del controllo frammento di codice.  Nota: il contenuto dei frammenti di codice con spazio "Non-Breaking" verrà modificato in spazio. |
| **Elemento** | **valore** |
| CopiaToClipboard | Copia negli Appunti |
| VisualizzazioneColoreTesto | Visualizza con colori |
| CombinedVBTabDisplayLanguage | Visual Basic (esempio)Visual Basic (Sample) |
| Dichiarazione VB | Dichiarazione |
| VBUsage (informazioni in lingua inlingua | Uso |
| Funzionalità: | **Feedback, piè di pagina e logo** |
| Usare: | Fornire un controllo di feedback per il cliente per fornire commenti e suggerimenti sull'argomento corrente tramite posta elettronica.  Testo di copyright per il contenuto.  Definizione del logo. |
| **Elemento** | **Valore (queste stringhe possono essere modificate per soddisfare le esigenze di adozione del contenuto).** |
| Copyright | © 2013 Microsoft Corporation. Tutti i diritti sono riservati. |
| SendCommentiesto | \<un href{0}" {1} "\<>Invia commenti e suggerimenti /a> su questo argomento a Microsoft. |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC (Nome File LogoHC) | vs_logo_wh.gif |
| Funzionalità: | **Dichiarazione di non responsabilità** |
| Usare: | Un insieme di dichiarazioni di non responsabilità specifiche del caso per il contenuto tradotto dal computer. |
| **Elemento** | **valore** |
| MT_Editable | Questo articolo è stato tradotto a macchina. Se si dispone di una connessione A Internet, selezionare "Visualizza questo argomento online" per visualizzare questa pagina in modalità modificabile con il contenuto originale in inglese allo stesso tempo. |
| MT_NonEditable | Questo articolo è stato tradotto a macchina. Se si dispone di una connessione A Internet, selezionare "Visualizza questo argomento online" per visualizzare questa pagina in modalità modificabile con il contenuto originale in inglese allo stesso tempo. |
| MT_QualityEditable | Questo articolo è stato tradotto manualmente. Se si dispone di una connessione A Internet, selezionare "Visualizza questo argomento online" per visualizzare questa pagina in modalità modificabile con il contenuto originale in inglese allo stesso tempo. |
| MT_QualityNonEditable | Questo articolo è stato tradotto manualmente. Se si dispone di una connessione A Internet, selezionare "Visualizza questo argomento online" per visualizzare questa pagina in modalità modificabile con il contenuto originale in inglese allo stesso tempo. |
| MT_BetaContents | Questo articolo è stato tradotto a macchina per un rilascio preliminare. Se si dispone di una connessione A Internet, selezionare "Visualizza questo argomento online" per visualizzare questa pagina in modalità modificabile con il contenuto originale in inglese allo stesso tempo. |
| MT_BetaRecycledContents | Questo articolo è stato tradotto manualmente per una versione preliminare. Se si dispone di una connessione A Internet, selezionare "Visualizza questo argomento online" per visualizzare questa pagina in modalità modificabile con il contenuto originale in inglese allo stesso tempo. |
| Funzionalità: | **Tabella Collegamento** |
| Usare: | Supporto per i collegamenti agli argomenti online |
| **Elemento** | **valore** |
| LinkTableTitle | Tabella dei collegamenti |
| TopicEnuLinkTesto | Visualizzare la\<versione inglese /a> di questo argomento disponibile nel computer. |
| ArgomentoOnlineLinkTesto | Visualizzare questo \<argomento un{0}href " " {1}>online\</a> |
| Testo online | Online |
| Funzionalità: | **Controllo audio video** |
| Usare: | Visualizzare elementi e testo per i contenuti video |
| **Elemento** | **valore** |
| MultiMediaNotSupported | Per supportare {0} il contenuto, è necessario installare Internet Explorer 9 o versione successiva. |
| Videotext | visualizzazione di video |
| Testo audio | audio in streaming |
| Testo OnlineVideoLinkText | \<p>Per visualizzare il video {0} \<associato a questo{1}argomento, fare clic su un href " ">{2}qui\</a>. \<> /p |
| Testo OnlineAudioLinkText | \<p>Per ascoltare l'audio associato {0} \<a questo{1}argomento, {2}\<fare clic su un href " ">qui /a>. \<> /p |
| Funzionalità: | **Controllo Contenuto non installato** |
| Usare: | Elementi di testo (stringhe) utilizzati per il rendering di contentnotinstalled.htm |
| **Elemento** | **valore** |
| ContentNotInstalledTitle | Non è stato trovato alcun contenuto nel computer. |
| ContentNotInstalledDownloadContentText | \<p>Per scaricare il \<contenuto sul{0}computer,>{1} fare\<clic sulla scheda Gestisci /a>. \<> /p |
| Testo ContenutoNotaLe | \<p>Nessun contenuto installato nel computer. Vedere l'amministratore per l'installazione del contenuto della Guida locale. \<> /p |
| Funzionalità: | **Controllo Argomento non trovato** |
| Usare: | Elementi di testo (stringhe) utilizzati per il rendering di topicnotfound.htm |
| **Elemento** | **valore** |
| TopicNotFoundTitle | Impossibile trovare l'argomento richiesto nel computer. |
| ArgomentoNotAVisualizzazioneVisualizzazioneOggettoTesto | \<p>L'argomento richiesto non è stato \<trovato nel computer, {1} ma è\<possibile utilizzare un href "{0}">visualizzare l'argomento online /a>. \<> /p |
| ArgomentoNotFoundDownloadContentText | \<p>Vedere il riquadro di \<spostamento per i{0} {1} collegamenti ad argomenti\<simili o un href ">fare clic sulla scheda Gestisci /a> per scaricare il contenuto nel computer. \<> /p |
| ArgomentoNotAtoTesto | \<p>L'argomento richiesto non è stato trovato nel computer. \<> /p |
| Funzionalità: | **Argomento Controllo danneggiato** |
| Usare: | Elementi di testo (stringhe) utilizzati per il rendering di topiccorrupted.htm |
| **Elemento** | **valore** |
| TopicCorruptedTitle | Impossibile visualizzare l'argomento richiesto. |
| ArgomentoCorruptedViewOnlineText | \<p>Visualizzatore della Guida non è in grado di visualizzare l'argomento richiesto. Potrebbe esserci un errore nel contenuto dell'argomento o una dipendenza di sistema sottostante. \<> /p |
| Funzionalità: | **Controllo Home Page** |
| Usare: | Testo che supporta la visualizzazione del contenuto del nodo di primo livello del Visualizzatore della Guida. |
| **Elemento** | **valore** |
| HomePageTitle | Home page del visualizzatore della Guida |
| HomePageIntroduzione | \<p>Benvenuti nel Visualizzatore della Guida Microsoft, una fonte essenziale di informazioni per tutti coloro che utilizzano strumenti, prodotti, tecnologie e servizi Microsoft. Il visualizzatore della Guida consente di accedere a informazioni su procedura e riferimento, codice di esempio, articoli tecnici e altro ancora. Per trovare il contenuto necessario, sfogliare il sommario, usare la ricerca full-text o spostarsi all'interno del contenuto usando l'indice delle parole chiave. \<> /p |
| HomePageContenutoInstallText | \<p \<>br />Utilizzare \<la{0} {1} scheda a\<href ">Gestisci\<contenuto \</a> per eseguire le operazioni seguenti: ul>li>Aggiungere contenuto al computer. \</li \<>li>Verificare la disponibilità di aggiornamenti per il contenuto locale. \</li \<>li>Rimuove il contenuto dal computer. \</li \<>/ul>\</p> |
| HomePageInstalledBooks | Libri installati |
| HomePageNoLibriinstallati | Non è stato trovato alcun contenuto nel computer. |
| HomePageHelpSettings | Impostazioni del contenuto della Guida |
| HomePageHelpSettingsText | \<p>L'impostazione corrente è la Guida locale. Nel Visualizzatore della Guida viene visualizzato il contenuto installato nel computer. \<br />Per modificare l'origine del contenuto della \<Guida, sulla{0}barra dei menu\<di Visual Studio, scegliere span style "" ">Help, Set Help Preference /span>. \<br />\</p> |
| MegaByte | MB |

**branding.js**

Il file branding.js contiene JavaScript utilizzato dagli elementi di personalizzazione del Visualizzatore della Guida di Visual Studio.  Di seguito è riportato un elenco degli elementi di personalizzazione e della funzione JavaScript di supporto.  Tutte le stringhe da localizzare per questo file sono definite nella sezione "Localizable Strings" all'inizio di questo file.  Il file ICL è stato creato per le stringhe loc all'interno del file branding.js.

||||
|-|-|-|
|**Caratteristica di personalizzazione**|**Funzione JavaScript**|**Descrizione**|
|Var...||Definire le variabili|
|Ottenere la lingua del codice utenteGet the user code language|setUserPreferenceLang (informazioni in lingua lingua inlingua in stato in|esegue il mapping di un indice al linguaggio del codice|
|Impostare e ottenere i valori dei cookie|getCookie, setCookie||
|Membro ereditato|changeMembersLabel (etichettadi changeMembers)|Espandi/comprimi membro ereditato|
|Quando SelfBranded- False|Onload|Leggere la stringa di query per verificare se si tratta di una richiesta di stampa.  Impostare tutti i frammenti di codice per mettere a fuoco la scheda preferita dall'utente.  Se si tratta di una richiesta di stampa, impostare isPrinterFriendly su true. Verificare la modalità a contrasto elevato.|
|Frammento di codiceCode Snippet|addSpecificTextLanguageTagSet||
||GetIndexFromDevLang (informazioni in lingua inlingua in stato inlingua).||
||ModificaScheda||
||setCodesnippetLang (informazioni in lingua inlingua inlinguaina||
||setCurrentLang (informazioni in lingua lingua inlingua in||
||CopiaToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|scrivere tutti gli oggetti di controllo comprimibili nell'elenco.|
||CA_Click|in base allo stato dell'area comprimibile, definisce l'immagine e il testo da presentare|
|Supporto del contrasto per Logo|isBlackBackground()|Chiamato per determinare se lo sfondo è nero.  Accurato solo in modalità a contrasto elevato.|
||isHighContrast()|utilizzare un intervallo colorato per rilevare la modalità a contrasto elevato|
||onHighContrast(nero)|Chiamato quando viene rilevato un contrasto elevato|
|Funzionalità LST|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Funzionalità MultiMedia|didascalia(inizio, fine, testo, stile)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(nodo)||
||styleRectify(styleName, styleValue)||
||showCC(id)||
||subtitle(id)||

**FILE HTM**

Il pacchetto di personalizzazione contiene un set di file HTM che supportano scenari per la comunicazione di informazioni chiave agli utenti del contenuto della Guida, ad esempio una home page contenente una sezione che descrive quali set di contenuto vengono installati e le pagine che indicano all'utente quando non è possibile trovare argomenti nell'insieme locale di argomenti. Questi file HTM possono essere modificati per prodotto.  I fornitori di ISO Shell sono in grado di prendere il pacchetto di branding predefinito e modificare il comportamento e il contenuto di queste pagine per soddisfare le loro esigenze.  Questi file fanno riferimento al rispettivo pacchetto di personalizzazione in modo che i tag di personalizzazione ottenere il contenuto corrispondente dal file branding.xml.

||||
|-|-|-|
|**File**|**Utilizzare**|**Origine contenuto visualizzata**|
|homepage.htm (pagina home)|Si tratta di una pagina che visualizza il contenuto attualmente installato e qualsiasi altro messaggio appropriato per presentare all'utente il contenuto.  Questo file ha l'attributo di metadati aggiuntivi "Microsoft.Help.Id" content "-1" che posiziona questo contenuto nella parte superiore del sommario del contenuto locale.||
||<META_HOME_PAGE_TITLE_ADD />|Branding.xml, \<tag HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|Branding.xml, \<tag HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.xml, \<tag HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|Sezione intestazione Branding.xml tag\<HomePageInstalledBooks>, \<i dati generati dall'applicazione, HomePageNoBooksInstalled> quando non sono installati libri.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|Sezione intestazione Branding.xml tag \<HomePageHelpSettings>, testo \<di sezione HomePageHelpSettingsText>.|
|topiccorrupted.htm|Quando un argomento esiste nel set locale, ma per qualche motivo non può essere visualizzato (contenuto danneggiato).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding.xml, \<tag TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding.xml, \<tag TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Quando un argomento non viene trovato nel set di contenuti locale, né disponibile online||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.xml, \<tag TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD />|Branding.xml, \<tag TopicNotFoundViewOnlineText \<> - TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD />|Branding.xml, \<tag TopicNotFoundText>|
|contentnotinstalled.htm|Quando non è installato alcun contenuto locale per il prodotto.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding.xml, \<tag ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding.xml, \<tag ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|Branding.xml, \<tag ContentNotInstalledText>|

**File CSS**

Il pacchetto di personalizzazione del visualizzatore della Guida di Visual Studio contiene due file css per supportare una presentazione coerente del contenuto della Guida di Visual Studio:The Visual Studio Help Viewer Branding Package contains two css files to support consistent Visual Studio Help content presentation:

- Branding.css - contiene gli elementi css per il rendering in cui SelfBranded

- Printer.css - contiene gli elementi css per il rendering in cui SelfBranded

I file Branding.css includono le definizioni per la presentazione dell'argomento\<di Visual Studio (caveat è che il file branding.css contenuto nel Branding_ le impostazioni locali>.mshc dal servizio del pacchetto possono cambiare).

**File grafici**

Il contenuto di Visual Studio visualizza un logo di Visual Studio e altri elementi grafici.  L'elenco completo dei file grafici nel pacchetto di personalizzazione del Visualizzatore della Guida di Visual Studio è illustrato di seguito.

||||
|-|-|-|
|**File**|**Utilizzare**|**Esempi**|
|clear.gif|Utilizzato per eseguire il rendering dell'area fascicolabile||
|footer_slice.gif|Presentazione del piè di pagina||
|info_icon.gif|Utilizzato per la visualizzazione delle informazioni|Dichiarazione di non responsabilità|
|online_icon.gif|Questa icona deve essere associata a link online||
|tabLeftBD.gif|Utilizzato per eseguire il rendering del contenitore di frammenti di codice||
|schedaRightBD.gif|Utilizzato per eseguire il rendering del contenitore di frammenti di codice||
|vs_logo_bk.gif|Utilizzato per i normali riferimenti al logo \<a contrasto come definito in Branding.xml tag LogoFileName>.  Per i prodotti Visual Studio, il nome del logo è vs_logo_bk.gif.||
|vs_logo_wh.gif|Utilizzato per i normali riferimenti ai \<logo alti come definito nel tag Branding.xml LogoFileNameHC>.  Per i prodotti Visual Studio, il nome del logo è vs_logo_wh.gif.||
|file ccOff.png|Immagine sottotitoli||
|CcOn.png|Immagine sottotitoli||
|ImageSprite.png|Utilizzato per eseguire il rendering dell'area fascicolabile|espanso o comprimigrafico|

## <a name="deploy-a-set-of-topics"></a>Distribuire un set di argomentiDeploy a set of topics

Si tratta di un'esercitazione semplice e rapida per la creazione di un set di distribuzione del contenuto del visualizzatore della Guida costituito da un file MSHA e dal set di file cab o MShC contenenti gli argomenti. MSHA è un file XML che descrive un set di file cab o MSHC. Il Visualizzatore della Guida può leggere il file MSHA per ottenere un elenco di contenuti (il file . CAB o . MSHC) disponibile per l'installazione locale.

Questo è solo un primer che descrive lo schema XML di base per il visualizzatore della Guida MSHA.  Di seguito è riportata un'implementazione di esempio in questa breve panoramica e nell'esempio HelpContentSetup.msha.There is an example implementation below this brief overview and sample HelpContentSetup.msha.

Il nome dell'MSHA, ai fini di questo primer, è HelpContentSetup.msha (il nome del file può essere qualsiasi cosa, con l'estensione . MSHA). HelpContentSetup.msha (esempio riportato di seguito) deve contenere un elenco dei cab o MSHC disponibili.  Il tipo di file deve essere coerente all'interno di MSHA (non supporta una combinazione di tipi di file MSHA e CAB). Per ogni CAB o MSHC, \<ci dovrebbe essere una classe div" >... \<> /div (vedere l'esempio seguente).

Nota: nell'esempio di implementazione riportato di seguito, abbiamo incluso il pacchetto di personalizzazione. Questo è fondamentale da includere per ottenere gli elementi di rendering del contenuto di Visual Studio necessari e i comportamenti del contenuto.

Esempio HelpContentSetup.msha file: (Sostituisci "nome set di contenuti 1" e "nome set di contenuti 2" e così via con i nomi dei file.)

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>.
```

1. Creare una cartella locale, ad esempio "C:"SampleContent"

2. Per questo esempio, useremo i file MSHC per contenere gli argomenti.  Un MSHC è un zip con l'estensione del file modificata da .zip a . mSHC.

3. Creare il file HelpContentSetup.msha seguente come file di testo (blocco note è stato utilizzato per creare il file) e salvarlo nella cartella indicata sopra (vedere il passaggio 1).

La classe "Branding" esiste ed è unica. Il Branding mshc è incluso in questo primer in modo che il contenuto installato avrà branding e i comportamenti di contenuto contenuti negli MShC avranno gli elementi di supporto appropriati contenuti nel pacchetto di personalizzazione. Senza questo, gli errori si verificano quando il sistema cerca gli elementi di supporto che non fanno parte del contenuto strappato (installato).

Per ottenere il pacchetto di personalizzazione di Visual Studio, copiare Branding_en-US.mshc nella cartella di lavoro.

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>
<div class="package">
<span class="packageType">branding</span>
<span class="name">Branding_en-US</span>
<span class="deployed">True</span>
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>
</div>
</div>
</body>
</html>
```

**Riepilogo**

L'utilizzo e l'estensione dei passaggi precedenti consentirà ai provider di servizi Condivisi di distribuire i set di contenuto per il Visualizzatore della Guida di Visual Studio.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Aggiungere la Guida a Visual Studio Shell (integrata e isolata)

**Introduzione**

In questa procedura dettagliata viene illustrato come incorporare il contenuto della Guida in un'applicazione Visual Studio Shell e quindi distribuirlo.

**Requisiti**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Redist shell isolata di Visual Studio 2013](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Panoramica**

[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell è una versione [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] dell'IDE su cui è possibile basare un'applicazione. Tali applicazioni contengono Isolated Shell insieme alle estensioni create. Utilizzare i modelli di progetto Isolated [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell, inclusi nell'SDK, per compilare le estensioni.

I passaggi di base per la creazione di un'applicazione basata su Isolated Shell e la relativa Guida:

1. Ottenere [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] il file isO Shell ridistribuibile (download Microsoft).

2. In Visual Studio creare un'estensione della Guida basata su Isolated Shell, ad esempio l'estensione della Guida Contoso descritta più avanti in questa procedura dettagliata.

3. Eseguire il wrapping dell'estensione e della shell ISO ridistribuibile in un file MSI di distribuzione (installazione di un'applicazione). Questa procedura dettagliata non include un passaggio di installazione.

Creare un archivio del contenuto di Visual Studio.Create a Visual Studio content store. Per lo scenario Shell integrata, modificare Visual Studio12 con il nome del catalogo prodotti come segue:

- Creare la cartella C:.

- Creare un file denominato CatalogType.xml e aggiungerlo alla cartella. Il file deve contenere le seguenti righe di codice:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Definire l'archivio del contenuto nel Registro di sistema. Per la shell integrata, modificare VisualStudio15 con il nome del catalogo prodotti:

- HKLM SOFTWARE Wow6432Node Microsoft , Guida , v2.3 , Cataloghi , Visual Studio15

   Chiave: valore della stringa LocationPath: C:

- HKLM SOFTWARE Wow6432Node Microsoft , Guida v2.3 , Cataloghi VisualStudio15 , en-US

   Chiave: CatalogName Valore [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] stringa: Documentazione

**Creare il progetto**

Per creare un'estensione Isolated Shell:

1. In Visual Studio, in **File**, scegliere **Nuovo progetto**, in **Altri tipi di progetto** scegliere **Estensibilità**, quindi **Scegliere Visual Studio Shell isolato**. Denominare `ContosoHelpShell`il progetto ) per creare un progetto di estensibilità basato sul modello Visual Studio Isolated Shell.

2. In Esplora soluzioni, nel progetto ContosoHelpShellUI, nella cartella File di risorse, aprire ApplicationCommands.vsct. Assicurarsi che questa riga sia commentata (ricerca di "No_Help"):`<!-- <define name="No_HelpMenuCommands"/> -->`

3. Premere F5 per compilare ed eseguire **Debug**. Nell'istanza sperimentale dell'IDE Isolated Shell, scegliere il menu **Guida.** Assicurarsi che siano visualizzati i comandi **Visualizza Guida**, Aggiungi e rimuovi contenuto **della Guida**e Imposta **preferenza Guida.**

4. In Esplora soluzioni, nel progetto ContosHelpShell, nella cartella Personalizzazione della shell, aprire ContosoHelpShell.pkgdef. Per definire il catalogo della Guida di Contoso, aggiungere le righe seguenti:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. In Esplora soluzioni, nel progetto ContosHelpShell, nella cartella Personalizzazione della shell, aprire ContosoHelpShell.Application.pkgdef. Per attivare la Guida F1, aggiungere le seguenti righe:

    ```
    // F1 Help Provider

    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="13407"
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"
    @="Help3 Provider"
    [$RootKey$\HelpProviders]
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="Help3 Provider"
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"
    ```

6. In Esplora soluzioni scegliere la voce di menu **Proprietà** dal menu di scelta rapida della soluzione ContosoHelpShell. In **Proprietà di configurazione**selezionare Gestione **configurazione**. Nella colonna **Configurazione** modificare ogni valore "Debug" in "Release".

7. Compilare la soluzione. In questo modo viene creato un set di file in una cartella di rilascio, che verrà utilizzato nella sezione successiva.

Per testare questo come se distribuito:

1. Nel computer in cui si distribuisce Contoso, installare la shell ISO scaricata (dall'alto).

2. Creare una \\cartella in , Programmi\\(x86) e denominarla `Contoso`.

3. Copiare il contenuto della cartella \\di rilascio ContosoHelpShell nella cartella .

4. Avviare l'Editor del Registro `Regedit`di sistema scegliendo **Esegui** nel menu **Start** e immettendo . Nell'editor del Registro di sistema scegliere **File**, quindi **Importa**. Passare alla cartella del progetto ContosoHelpShell. Nella sottocartella ContosoHelpShell scegliere ContosoHelpShell.reg.

5. Creare un archivio del contenuto:Create a content store:

    Per ISO Shell - creare un archivio del contenuto di Contoso C:

    Per [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] la shell integrata, creare la cartella C:

6. Creare CatalogType.xml e aggiungerlo all'archivio del contenuto (passaggio precedente) contenente:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Aggiungere le seguenti chiavi del Registro di sistema:

    HKLM SOFTWARE Wow6432Node Microsoft , Guida v2.3 , Cataloghi VisualStudio15Key: valore stringa LocationPath :

    Per isO Shell:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Shell integrata:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Chiave: Valore stringa [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] CatalogName: Documentazione. Per ISO Shell, questo è il nome del catalogo.

8. Copiare il contenuto (cabs o MSHC e MSHA) in una cartella locale.

9. Esempio di riga di comando della shell integrata per il test dell'archivio del contenuto. Per ISO Shell, modificare i valori del catalogo e launchingApp in base alle esigenze del prodotto.

     "C: (x86) file di programma (x86) Microsoft Help Viewer v2.3 HlpViewer.exe" /catalogName VisualStudio15 /helpQuery method " pagina&id ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. Avviare l'applicazione Contoso (dalla radice dell'app Contoso). All'interno di ISO Shell, scegliere la voce di menu **Guida** e modificare la **preferenza Imposta preferenza della Guida** in Usa Guida **locale**.

11. All'interno della shell, scegliere la voce di menu **Guida** , quindi **Visualizza Guida**. Il visualizzatore della Guida locale dovrebbe avviarsi. Scegliere la scheda **Gestisci contenuto.** In **Origine installazione**scegliere il pulsante di opzione **Disco.** Scegliere il pulsante **...** e passare alla cartella locale contenente il contenuto di Contoso (copiato nella cartella locale nel passaggio precedente). Scegliere HelpContentSetup.msha. Contoso dovrebbe ora essere visualizzato come libro nelle selezioni del libro. Scegliere **Aggiungi**, quindi il pulsante **Aggiorna** (in basso a destra).

12. Nell'IDE di Contoso scegliere il tasto F1 per testare la funzionalità F1.

## <a name="additional-resources"></a>Risorse aggiuntive

Per l'API Runtime, vedere [API della Guida di Windows](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Per ulteriori informazioni su come sfruttare l'API della Guida, vedere Esempi di codice del [Visualizzatore della Guida.](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples)

Puoi inviare suggerimenti di funzionalità nella [community degli sviluppatori.](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)
