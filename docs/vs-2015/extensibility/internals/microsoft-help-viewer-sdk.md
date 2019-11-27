---
title: SDK di Microsoft Help Viewer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 34
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cafdfacec24e906569d0f2b0d1a334511a75e30a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300719"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Questo articolo contiene le attività seguenti per gli integratori del Visualizzatore della Guida di Visual Studio:

- Creazione di un argomento (supporto F1)

- Creazione di un pacchetto di personalizzazione del contenuto di Help Viewer

- Distribuzione di un set di articoli

- Aggiunta della Guida alla shell di Visual Studio (integrata o isolata)

- Risorse aggiuntive

### <a name="creating-a-topic-f1-support"></a>Creazione di un argomento (supporto F1)
 In questa sezione viene fornita una panoramica dei componenti di un argomento presentato, dei requisiti dell'argomento, una breve descrizione di come creare un argomento (inclusi i requisiti di supporto F1) e infine un argomento di esempio con il risultato di cui è stato eseguito il rendering.

 **Panoramica dell'argomento del Visualizzatore della Guida**

 Quando un argomento viene chiamato per il rendering, il Visualizzatore della guida ottiene gli elementi del pacchetto di personalizzazione associati all'argomento al momento dell'installazione o dell'ultimo aggiornamento, insieme all'argomento XHTML, e combina i due risultati nella visualizzazione del contenuto presentata (dati di personalizzazione + dati dell'argomento).  Il pacchetto di personalizzazione contiene i loghi, il supporto per i comportamenti del contenuto e il testo di personalizzazione (copyright e così via).  Vedere "creazione di un pacchetto di personalizzazione" di seguito per altre informazioni sugli elementi del pacchetto di personalizzazione.  Nel caso in cui non sia stato associato alcun pacchetto di personalizzazione all'argomento, Help Viewer utilizzerà il pacchetto di personalizzazione di fallback presente nella radice dell'applicazione Help Viewer (Branding_en-US. mshc).

 **Requisiti per gli argomenti del Visualizzatore della Guida**

 Per il rendering corretto nel Visualizzatore della guida, il contenuto dell'argomento non elaborato deve essere di W3C Basic 1,1 XHTML.

 Un argomento contiene in genere due sezioni:

- Metadati (vedere informazioni di riferimento sui metadati del contenuto): dati sull'argomento, ad esempio l'ID univoco dell'argomento, il valore della parola chiave, l'ID Sommario dell'argomento, l'ID del nodo padre e così via.

- Contenuto del corpo: conforme a W3C Basic 1,1 XHTML, che include i comportamenti del contenuto supportati (area comprimibile, frammento di codice e così via). Di seguito è riportato un elenco completo.

  Controlli supportati del pacchetto di personalizzazione di Visual Studio:

- Collegamenti

- CodeSnippet

- CollapsibleArea

- Membro ereditato

- LanguageSpecificText

  Stringhe di lingua supportate (senza distinzione tra maiuscole e minuscole):

- javascript

- CSharp o c #

- cplusplus o VisualC + + o c++

- JScript

- VisualBasic o VB

- f # o FSharp o FS

- other: stringa che rappresenta un nome di lingua

  **Creazione di un argomento del Visualizzatore della Guida**

  Creare un nuovo documento XHTML denominato ContosoTopic4. htm e includere il tag title (sotto).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

 Aggiungere quindi i dati per definire il modo in cui l'argomento deve essere presentato (autofirmato o meno), come fare riferimento a questo argomento per F1, in cui questo argomento esiste nel sommario, il relativo ID (per riferimento al collegamento da altri argomenti) e così via.  Per un elenco completo dei metadati supportati, vedere la tabella "metadati del contenuto" riportata di seguito.

- In questo caso, verrà usato il pacchetto di personalizzazione, una variante del pacchetto di personalizzazione del Visualizzatore della Guida di Visual Studio.

- Aggiungere il nome e il valore F1 ("Microsoft. Help. F1" Content = "ContosoTopic4") che corrisponderanno al valore F1 specificato nell'elenco proprietà IDE.  Per ulteriori informazioni, vedere la sezione supporto F1.   Si tratta del valore corrispondente alla chiamata F1 dall'interno dell'IDE per visualizzare questo argomento quando si sceglie F1 nell'IDE.

- Aggiungere l'ID argomento. Si tratta della stringa utilizzata da altri argomenti per il collegamento a questo argomento.  Si tratta dell'ID del Visualizzatore della Guida per questo argomento.

- Per il sommario, aggiungere il nodo padre di questo argomento per definire il punto in cui verrà visualizzato il nodo del sommario dell'argomento.

- Per il sommario, aggiungere l'ordine dei nodi di questo argomento. Quando il nodo padre ha n numero di nodi figlio, definire nell'ordine dei nodi figlio il percorso dell'argomento. Questo argomento, ad esempio, è costituito dal numero 4 di 4 argomenti figlio.

  Sezione metadati di esempio:

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

 **Corpo dell'argomento**

 Il corpo (escluso l'intestazione e il piè di pagina) dell'argomento conterrà i collegamenti alle pagine, una sezione di nota, un'area comprimibile, un frammento di codice e una sezione di testo specifico del linguaggio.  Per informazioni sulle aree dell'argomento presentato, vedere la sezione relativa alla personalizzazione.

1. Aggiungere un tag titolo argomento: `<div class="title">Contoso Topic 4</div>`

2. Aggiungere una sezione Nota: `<div class="alert"> add your table tag and text </div>`

3. Aggiungere un'area comprimibile: `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Aggiungere un frammento di codice: `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Aggiungere testo specifico per il linguaggio di codice: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` si noti che devLangnu = consente di immettere altre lingue. Ad esempio, devLangnu = "FORTRAN" visualizzerà FORTRAN quando il frammento di codice DisplayLanguage = FORTRAN

6. Aggiungi collegamenti alla pagina: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Nota: per la nuova colorazione del codice "lingua di visualizzazione" ( F#ad esempio, COBOL, Fortran) non supportata nel frammento di codice, sarà monocromatico.

 **Argomento del Visualizzatore della Guida di esempio** Il codice illustra come definire i metadati, un frammento di codice, un'area comprimibile e un testo specifico del linguaggio.

```
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
<li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li>
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
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>

```

 **Supporto F1**

 In Visual Studio la selezione di F1 genera valori forniti dal posizionamento del cursore all'interno dell'IDE e popola un "contenitore delle proprietà" con i valori forniti (in base alla posizione del cursore. Quando il cursore è sopra la funzionalità x, la funzionalità x è attiva/attiva e popola il contenitore delle proprietà con i valori.  Quando si seleziona F1, viene popolato il contenitore delle proprietà e il codice di Visual Studio F1 verifica se l'origine della guida predefinita Customers è locale o online (online è l'impostazione predefinita), quindi crea la stringa appropriata in base all'impostazione Users (online è l'impostazione predefinita): Shell Execute (vedere la guida dell'amministratore della Guida per i parametri di avvio di exe) con i parametri per il Visualizzatore della guida locale + le parole chiave dall'elenco proprietà se la guida locale è l'impostazione predefinita o l'URL MSDN con la parola chiave nell'elenco dei parametri.

 Se vengono restituite tre stringhe per F1, denominate stringa multivalore, eseguire il primo termine, cercare un hit e, se viene trovato, l'operazione è stata eseguita. in caso contrario, passare alla stringa successiva.  L'ordine è importante. La presentazione delle parole chiave multivalore deve essere la stringa più lunga della stringa più breve.  Per verificare questa situazione nel caso di parole chiave multivalore, osservare la stringa dell'URL F1 online, che include la parola chiave scelta.

 In Visual Studio 2012 abbiamo intenzionalmente deciso una divisione tra online e offline, in modo che, se l'impostazione dell'utente fosse per la modalità online, abbiamo semplicemente passato la richiesta F1 direttamente al servizio query online su MSDN anziché al routing tramite l'agente della libreria della Guida in Visual Studio 2010. Si basa quindi su uno stato "fornitore contenuto installato = true" per determinare se eseguire un'operazione diversa in tale contesto. Se true, la logica di analisi e routing viene eseguita a seconda di ciò che si desidera supportare per i clienti. Se false, è sufficiente passare a MSDN. Se l'impostazione dell'utente è locale, tutte le chiamate vengono indirizzate al motore della guida locale.

 Diagramma di flusso F1:

 ![Flusso F1](../../extensibility/internals/media/f1flow.png "F1flow")

 Quando l'origine del contenuto della guida predefinita del Visualizzatore della guida è impostata su online (avvia nel browser):

- Le funzionalità del partner Visual Studio (VSP) emettono un valore per il contenitore delle proprietà F1 (prefisso del contenitore delle proprietà e URL online per il prefisso trovato nel registro di sistema): F1 Invia un URL VSP + parametri al browser.

- Funzionalità di Visual Studio (editor di linguaggio, voci di menu specifiche di Visual Studio e così via): F1 Invia un URL di Visual Studio al browser.

  Quando l'origine del contenuto della guida predefinita del Visualizzatore della guida è impostata su guida locale (avvia in Help Viewer):

- Funzionalità VSP in cui la parola chiave corrisponde tra il contenitore delle proprietà F1 e l'indice dell'archivio locale (ovvero, il prefisso del contenitore delle proprietà. keyword = il valore trovato nell'indice dell'archivio locale): F1 esegue il rendering dell'argomento nel Visualizzatore della guida.

- Funzionalità di Visual Studio (nessuna opzione per il VSP per l'override del contenitore delle proprietà emesso dalle funzionalità di Visual Studio): F1 esegue il rendering di un argomento di Visual Studio nel Visualizzatore della guida.

  Impostare i seguenti valori del registro di sistema per abilitare il fallback F1 per il contenuto della guida fornitore. Il fallback F1 significa che il Visualizzatore della guida è impostato in modo da cercare il contenuto della Guida F1 online e il contenuto del fornitore viene installato localmente sul disco rigido degli utenti. Il Visualizzatore della guida dovrebbe esaminare la guida locale per il contenuto anche se l'impostazione predefinita è per la Guida in linea.

1. Impostare il valore **VendorContent** nella chiave del registro di sistema della Guida 2,1:

   - Per i sistemi operativi a 32 bit:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent"=dword:00000001

   - Per i sistemi operativi a 64 bit:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent"=dword:00000001

2. Registrare lo spazio dei nomi del partner nella chiave del registro di sistema della Guida 2,1:

   - Per i sistemi operativi a 32 bit:

      HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Help\v2.1\Partner<em>\\< spazio dei nomi\></em>

      "location" = "offline"

   - Per i sistemi operativi a 64 bit:

      HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Partner<em>\\< spazio dei nomi\></em>

      "location" = "offline"

   **Analisi dello spazio dei nomi nativo di base**

   Per attivare l'analisi dello spazio dei nomi nativo di base, nel registro di sistema aggiungere un nuovo valore DWORD con il nome: BaseNativeNamespaces e impostare il relativo valore su 1 (sotto la chiave del catalogo che si desidera supportare).  Se ad esempio si vuole usare il catalogo di Visual Studio, è possibile aggiungere la chiave al percorso:

   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   Quando viene rilevata una parola chiave F1 nel metodo o nell'intestazione del formato, il carattere '/' verrà analizzato, ottenendo il costrutto seguente:

- HEADER: sarà lo spazio dei nomi che può essere usato per la registrazione nel registro di sistema

- METHOD: questa diventerà la parola chiave che viene passata.

  Ad esempio, data una libreria personalizzata denominata CustomLibrary e un metodo denominato MyTestMethod, quando viene ricevuta una richiesta F1 verrà formattata come `CustomLibrary/MyTestMethod`.

  Un utente può quindi registrare CustomLibrary come spazio dei nomi nell'hive partner e fornire la chiave di posizione desiderata e la parola chiave passata alla query sarà MyTestMethod.

  **Abilitare lo strumento di debug della guida nell'IDE**

  Aggiungere la chiave e il valore del registro di sistema seguenti:

  HKEY_CURRENT_USER chiave della Guida \Software\Microsoft\VisualStudio\12.0\Dynamic: Visualizza l'output del debug nel valore finale: Sì

  Nell'IDE, nella voce di menu della guida, selezionare "debug Guida contesto".

  **Metadati del contenuto**

  Nella tabella seguente, qualsiasi stringa visualizzata tra parentesi quadre è un segnaposto che deve essere sostituito da un valore riconosciuto. Ad esempio, in \<meta nome = "Microsoft. Help. locale" Content = "[Language Code]"/>, "[Language Code]" deve essere sostituito da un valore come "en-US".

|Proprietà (rappresentazione HTML)|Descrizione|
|--------------------------------------|-----------------|
|\< meta Name = "Microsoft. Help. locale" Content = "[Language-Code]"/>|Imposta le impostazioni locali per questo argomento. Se questo tag viene usato in un argomento, deve essere usato una sola volta e deve essere inserito sopra qualsiasi altro tag della Guida Microsoft. Se questo tag non viene utilizzato, il testo del corpo dell'argomento viene indicizzato utilizzando il Word breaker associato alle impostazioni locali del prodotto, se specificato. in caso contrario, viene usato il Word breaker en-US. Questo tag è conforme a ISOC RFC 4646. Per assicurarsi che la Guida Microsoft funzioni correttamente, utilizzare questa proprietà anziché l'attributo generale del linguaggio.|
|\< meta Name = "Microsoft. Help. TopicLocale" Content = "[Language-Code]"/>|Imposta le impostazioni locali per questo argomento quando vengono utilizzate anche altre impostazioni locali. Se questo tag viene usato in un argomento, deve essere usato una sola volta. Utilizzare questo tag quando il catalogo contiene contenuto in più di una lingua. Più argomenti in un catalogo possono avere lo stesso ID, ma ognuno deve specificare un TopicLocale univoco. L'argomento che specifica una TopicLocale che corrisponde alle impostazioni locali del catalogo è quello visualizzato nel sommario. Tuttavia, tutte le versioni in lingua dell'argomento vengono visualizzate nei risultati della ricerca.|
|titolo \< > [title]\</title >|Specifica il titolo di questo argomento. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. Se il corpo dell'argomento non contiene un titolo \<sezione div >, questo titolo viene visualizzato nell'argomento e nel sommario.|
|\< meta Name = "Microsoft. Help. Keywords" Content = "[aKeywordPhrase]"/>|Specifica il testo di un collegamento visualizzato nel riquadro indice del Visualizzatore della guida. Quando si fa clic sul collegamento, viene visualizzato l'argomento. È possibile specificare più parole chiave di indice per un argomento oppure omettere questo tag se non si desidera che i collegamenti a questo argomento vengano visualizzati nell'indice. Le parole chiave "K" di versioni precedenti della guida possono essere convertite in questa proprietà.|
|\< meta Name = "Microsoft. Help. ID" Content = "[TopicID]"/>|Imposta l'identificatore per questo argomento. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. L'ID deve essere univoco tra gli argomenti del catalogo con le stesse impostazioni locali. In un altro argomento è possibile creare un collegamento a questo argomento usando questo ID.|
|\< meta Name = "Microsoft. Help. F1" Content = "[System. Windows. Controls. Primitives. IRecyclingItemContainerGenerator]"/>|Specifica la parola chiave F1 per questo argomento. È possibile specificare più parole chiave F1 per un argomento oppure omettere questo tag se non si desidera che questo argomento venga visualizzato quando un utente dell'applicazione preme F1. In genere, per un argomento viene specificata solo una parola chiave F1. Le parole chiave "F" di versioni precedenti della guida possono essere convertite in questa proprietà.|
|\< meta Name = "Description" Content = "[Descrizione argomento]"/>|Fornisce un breve riepilogo del contenuto di questo argomento. Se questo tag viene usato in un argomento, deve essere usato una sola volta. A questa proprietà è possibile accedere direttamente dalla libreria di query; non è archiviato nel file di indice.|
 meta name="Microsoft.Help.TocParent" content="[parent_Id]"/>|Specifica l'argomento padre di questo argomento nel sommario. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. Il valore è Microsoft.Help.Id dell'elemento padre. Un argomento può avere una sola posizione nel sommario. "-1" è considerato l'ID argomento per la radice del sommario. In [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)], la pagina è home page Visualizzatore della guida. Questo è lo stesso motivo per cui si aggiunge in modo specifico TocParent =-1 ad alcuni argomenti per assicurarsi che vengano visualizzati al livello principale. Il Visualizzatore della guida home page è una pagina di sistema e pertanto non può essere sostituita. Se un VSP tenta di aggiungere una pagina con ID-1, è possibile che venga aggiunta al set di contenuti, ma Help Viewer utilizzerà sempre la pagina System-Help Viewer Home|
|\< meta Name = "Microsoft. Help. tocorder" Content = "[Integer positivo]"/>|Specifica la posizione del sommario in questo argomento rispetto ai relativi argomenti peer. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. Il valore è un numero intero. Un argomento che specifica un numero intero di valore inferiore viene visualizzato sopra un argomento che specifica un numero intero di valore superiore.|
|\< meta Name = "Microsoft. Help. Product" Content = "[Codice prodotto]"/>|Specifica il prodotto descritto in questo argomento. Se questo tag viene usato in un argomento, deve essere usato una sola volta. Queste informazioni possono essere fornite anche come parametro passato all'indicizzatore della guida.|
|\< meta Name = "Microsoft. Help. ProductVersion" Content = "[numero di versione]"/>|Specifica la versione del prodotto descritta in questo argomento. Se questo tag viene usato in un argomento, deve essere usato una sola volta. Queste informazioni possono essere fornite anche come parametro passato all'indicizzatore della guida.|
|\< meta Name = "Microsoft. Help. Category" Content = "[String]"/>|Utilizzato dai prodotti per identificare le sottosezioni del contenuto. È possibile identificare più sottosezioni per un argomento oppure omettere questo tag se non si desidera che i collegamenti identifichino le sottosezioni. Questo tag viene usato per archiviare gli attributi per TARGETOS e TargetFrameworkMoniker quando un argomento viene convertito da una versione precedente della guida. Il formato del contenuto è attributeName: AttributeValue.|
|\< meta Name = "Microsoft. Help. TopicVersion content =" [numero di versione argomento] "/>|Specifica la versione dell'argomento in cui sono presenti più versioni in un catalogo. Poiché non è garantito che Microsoft.Help.Id sia univoco, questo tag è obbligatorio quando più di una versione di un argomento è presente in un catalogo, ad esempio quando un catalogo contiene un argomento per la .NET Framework 3,5 e un argomento per il .NET Framework 4 ed entrambi hanno lo stesso micro temporanea. Help.Id.|
|\< meta Name = "SelfBranded" Content = "[TRUE o FALSE]"/>|Specifica se in questo argomento viene utilizzato il pacchetto di personalizzazione per l'avvio di gestione librerie della guida o un pacchetto di personalizzazione specifico per l'argomento. Questo tag deve essere TRUE o FALSE. Se il valore è TRUE, il pacchetto di personalizzazione per l'argomento associato sostituisce il pacchetto di personalizzazione impostato al momento dell'avvio di gestione librerie della guida, in modo che venga eseguito il rendering dell'argomento come previsto anche se si differenzia dal rendering di altro contenuto. Se è FALSE, viene eseguito il rendering dell'argomento corrente in base al pacchetto di personalizzazione impostato al momento dell'avvio di gestione librerie della guida. Per impostazione predefinita, gestione librerie della guida presuppone che la personalizzazione automatica sia false a meno che la variabile SelfBranded non sia dichiarata come TRUE; non è pertanto necessario dichiarare \<meta Name = "SelfBranded" Content = "FALSE"/>.|

### <a name="creating-a-branding-package"></a>Creazione di un pacchetto di personalizzazione
 La versione di Visual Studio include una serie di diversi prodotti Visual Studio, tra cui le shell isolate e integrate per i partner di Visual Studio.  Ognuno di questi prodotti richiede un certo livello di supporto per la personalizzazione del contenuto basato su argomenti, univoco per il prodotto.  Gli argomenti di Visual Studio, ad esempio, devono avere una presentazione del marchio coerente, mentre SQL Studio, che esegue il wrapping della shell ISO, richiede una personalizzazione univoca del contenuto della Guida per ogni argomento.  Un partner Shell integrato potrebbe volere che gli argomenti della guida siano all'interno del contenuto della guida del prodotto Visual Studio padre, mantenendo al tempo stesso la personalizzazione degli argomenti.

 I pacchetti di personalizzazione vengono installati dal prodotto che contiene il Visualizzatore della guida.  Per i prodotti Visual Studio:

- Un pacchetto di personalizzazione di fallback (Branding_\<impostazioni locali >. mshc) viene installato nella radice dell'app Help Viewer 2,1 (ad esempio: C:\Programmi (x86) \Microsoft Help Viewer\v2.1) dal Language Pack del Visualizzatore della guida.  Viene usato per i casi in cui il pacchetto di personalizzazione del prodotto non è installato (nessun contenuto è stato installato) o in cui il pacchetto di personalizzazione installato è danneggiato.  Gli elementi di Visual Studio (logo e feedback) vengono ignorati quando si usa il pacchetto di personalizzazione del fallback radice dell'app.

- Quando il contenuto di Visual Studio viene installato dal servizio del pacchetto di contenuto, viene installato anche un pacchetto di personalizzazione (per il primo scenario di installazione del contenuto).  Se è presente un aggiornamento per il pacchetto di personalizzazione, l'aggiornamento viene installato quando si verifica l'azione successiva per l'aggiornamento del contenuto o l'installazione di pacchetti aggiuntivi.

  Il Microsoft Help Viewer supporta la personalizzazione degli argomenti in base ai metadati dell'argomento.

- Dove i metadati dell'argomento definiscono autobranded = true, eseguono il rendering dell'argomento così come sono, non eseguono alcuna operazione (per quanto riguarda la personalizzazione).

- Dove i metadati dell'argomento definiscono autobranded = false, usare il pacchetto di personalizzazione associato al valore dei metadati TopicVendor.

- Dove i metadati dell'argomento definiscono Name = "Microsoft. Help. TopicVendor" Content =\< nome del pacchetto di personalizzazione in vendor MSHA >, usare il pacchetto di personalizzazione definito nel valore del contenuto.

- All'interno del catalogo di Visual Studio, esiste un'applicazione prioritaria per i pacchetti di personalizzazione.  Viene applicata la personalizzazione predefinita di Visual Studio, quindi, se definito nei metadati dell'argomento e supportato con il pacchetto di personalizzazione associato (come definito nel MSHA di installazione), il marchio definito dal fornitore viene applicato come sostituzione.

  Gli elementi di personalizzazione in genere rientrano in tre categorie principali:

- Elementi di intestazione (ad esempio, collegamento feedback, testo Disclaimer condizionale, logo)

- Comportamenti del contenuto (ad esempio espandere/comprimere elementi di testo di controllo ed elementi dei frammenti di codice)

- Elementi piè di pagina (ad esempio, copyright)

  Gli elementi considerati come elementi personalizzati includono (informazioni dettagliate in questa specifica):

- Logo catalogo/prodotto (ad esempio, Visual Studio)

- Collegamento feedback ed elementi di posta elettronica

- Testo della dichiarazione di non responsabilità

- Testo copyright

  I file di supporto nel pacchetto di personalizzazione del Visualizzatore della Guida di Visual Studio includono:

- Grafica (logo, icone e così via)

- Branding. js: file script che supportano i comportamenti del contenuto

- Branding. XML: stringhe utilizzate in modo coerente nel contenuto del catalogo.  Nota: per gli elementi di testo di localizzazione di Visual Studio nel file Branding. XML, includere _locID = "\<valore univoco >"

- Personalizzazione. CSS-definizioni di stile per la coerenza di presentazione

- Stampa. CSS-definizioni di stile per una presentazione stampata coerente

  Come indicato in precedenza, i pacchetti di personalizzazione sono associati all'argomento:

- Quando SelfBranded = false viene definito nei metadati, l'argomento eredita il pacchetto di personalizzazione del catalogo

- Oppure quando SelfBranded = false ed è presente un pacchetto di personalizzazione univoco definito in MSHA e disponibile quando il contenuto è installato

  Per VSPs implementazione di pacchetti di personalizzazione personalizzati (contenuto VSP, SelfBranded = true), un modo per procedere consiste nell'iniziare con il pacchetto di personalizzazione di fallback (installato con il Visualizzatore della guida) e modificare il nome del file in base alle esigenze.  Il Branding_\<impostazioni locali > file. mshc è un file zip con l'estensione di file modificato in. mshc, quindi è sufficiente modificare l'estensione da. mshc a. zip ed estrarre il contenuto.  Vedere di seguito per gli elementi del pacchetto di personalizzazione e modificare in base alle esigenze (ad esempio, modificare il logo nel logo VSP e il riferimento al logo nel file Branding. XML, aggiornare la personalizzazione. XML per le specifiche di VSP e così via).

  Al termine di tutte le modifiche, creare un file zip contenente gli elementi di personalizzazione desiderati e modificare l'estensione in. mshc.

  Per associare il pacchetto di personalizzazione personalizzato, creare il MSHA, che contiene il riferimento al file mshc di personalizzazione insieme al contenuto mshc (contenente gli argomenti).  Vedere di seguito "MSHA" per informazioni su come creare un MSHA di base.

  Il file Branding. XML contiene un elenco di elementi utilizzati per il rendering coerente di elementi specifici in un argomento quando l'argomento contiene \<meta Name = "Microsoft. Help. SelfBranded" Content = "false"/>.  Di seguito è riportato l'elenco di elementi di Visual Studio nel file Branding. XML.  Questo elenco è destinato a essere usato come modello per gli adopter della shell ISO, in cui tali elementi vengono modificati (ad esempio logo, feedback e copyright) per soddisfare le proprie esigenze di personalizzazione del prodotto.

  Nota: le variabili indicate da "{n}" presentano dipendenze del codice. la rimozione o la modifica di questi valori provocherà errori ed eventualmente arresti anomali dell'applicazione. Gli identificatori di localizzazione (ad esempio _locID = "CodeSnippet. n") sono inclusi nel pacchetto di personalizzazione di Visual Studio.

  **Personalizzazione. XML**

|||
|-|-|
|Funzionalità:|**CollapsibleArea**|
|Utilizzare:|Espandi Comprimi testo controllo contenuto|
|**Elemento**|**Valore**|
|ExpandText|Espandi|
|CollapseText|Comprimi|
|Funzionalità:|**CodeSnippet**|
|Utilizzare:|Testo del controllo frammento di codice.  Nota: il contenuto dei frammenti di codice con spazio "senza interruzioni" verrà modificato in spazio.|
|**Elemento**|**Valore**|
|CopyToClipboard|Copia negli Appunti|
|ViewColorizedText|Visualizza colori|
|CombinedVBTabDisplayLanguage|Visual Basic (esempio)|
|VBDeclaration|Dichiarazione|
|VBUsage|Utilizzo|
|Funzionalità:|**Feedback, piè di pagina e logo**|
|Utilizzare:|Fornire un controllo feedback per il cliente per fornire commenti e suggerimenti sull'argomento corrente tramite posta elettronica.  Testo del copyright per il contenuto.  Definizione del logo.|
|**Elemento**|**Valore (queste stringhe possono essere modificate per soddisfare le esigenze di adozione del contenuto).**|
|CopyRight|© 2013 Microsoft Corporation. Tutti i diritti sono riservati.|
|SendFeedback|\<a href = "{0}" {1}> inviare commenti e suggerimenti\</a > in questo argomento a Microsoft.|
|FeedbackLink||
|LogoTitle|[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]|
|LogoFileName|vs_logo_bk.gif|
|LogoFileNameHC|vs_logo_wh.gif|
|Funzionalità:|**Non responsabilità**|
|Utilizzare:|Set di dichiarazioni di non responsabilità del case specifiche per il contenuto tradotto dal computer.|
|**Elemento**|**Valore**|
|MT_Editable|Questo articolo è stato tradotto dal computer. Se si dispone di una connessione Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità modificabile con il contenuto originale in lingua inglese nello stesso momento.|
|MT_NonEditable|Questo articolo è stato tradotto dal computer. Se si dispone di una connessione Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità modificabile con il contenuto originale in lingua inglese nello stesso momento.|
|MT_QualityEditable|Questo articolo è stato tradotto manualmente. Se si dispone di una connessione Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità modificabile con il contenuto originale in lingua inglese nello stesso momento.|
|MT_QualityNonEditable|Questo articolo è stato tradotto manualmente. Se si dispone di una connessione Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità modificabile con il contenuto originale in lingua inglese nello stesso momento.|
|MT_BetaContents|Questo articolo è stato tradotto per un rilascio preliminare. Se si dispone di una connessione Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità modificabile con il contenuto originale in lingua inglese nello stesso momento.|
|MT_BetaRecycledContents|Questo articolo è stato tradotto manualmente per una versione preliminare. Se si dispone di una connessione Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità modificabile con il contenuto originale in lingua inglese nello stesso momento.|
|Funzionalità:|**LinkTable**|
|Utilizzare:|Supporto per i collegamenti agli argomenti online|
|**Elemento**|**Valore**|
|LinkTableTitle|Tabella di collegamento|
|TopicEnuLinkText|Visualizzare la versione in lingua inglese\</a > di questo argomento disponibile nel computer.|
|TopicOnlineLinkText|Vedere questo argomento \<a href = "{0}" {1}> online\</a >|
|OnlineText|Online|
|Funzionalità:|**Controllo audio video**|
|Utilizzare:|Visualizzazione di elementi e testo per il contenuto video|
|**Elemento**|**Valore**|
|MultiMediaNotSupported|Per supportare {0} contenuto, è necessario che sia installato Internet Explorer 9 o versione successiva.|
|VideoText|visualizzazione di video|
|AudioText|streaming audio|
|OnlineVideoLinkText|\<p > per visualizzare il video associato a questo argomento, fare clic su {0}\<a href = "{1}" >{2}qui\</a >.\</p >|
|OnlineAudioLinkText|\<p > per restare in ascolto dell'audio associato a questo argomento, fare clic su {0}\<a href = "{1}" >{2}qui\</a >.\</p >|
|Funzionalità:|**Controllo contenuto non installato**|
|Utilizzare:|Elementi di testo (stringhe) usati per il rendering di contentnotinstalled. htm|
|**Elemento**|**Valore**|
|ContentNotInstalledTitle|Nessun contenuto trovato nel computer.|
|ContentNotInstalledDownloadContentText|\<p > per scaricare il contenuto nel computer, \<a href = "{0}" {1}> fare clic sulla scheda Gestisci\</a >.\</p >|
|ContentNotInstalledText|\<p > nessun contenuto è installato nel computer. Vedere l'amministratore per l'installazione del contenuto della guida locale.\</p >|
|Funzionalità:|**Controllo argomento non trovato**|
|Utilizzare:|Elementi di testo (stringhe) usati per il rendering di topicnotfound. htm|
|**Elemento**|**Valore**|
|TopicNotFoundTitle|Impossibile trovare l'argomento richiesto nel computer.|
|TopicNotFoundViewOnlineText|\<p > l'argomento richiesto non è stato trovato nel computer, ma è possibile \<a href = "{0}" {1}> visualizzare l'argomento online\</a >.\</p >|
|TopicNotFoundDownloadContentText|\<p > vedere il riquadro di spostamento per i collegamenti ad argomenti simili oppure \<a href = "{0}" {1}> fare clic sulla scheda Gestisci\</a > per scaricare il contenuto nel computer.\</p >|
|TopicNotFoundText|\<p > l'argomento richiesto non è stato trovato nel computer.\</p >|
|Funzionalità:|**Controllo dell'argomento danneggiato**|
|Utilizzare:|Elementi di testo (stringhe) usati per il rendering di topiccorrupted. htm|
|**Elemento**|**Valore**|
|TopicCorruptedTitle|Impossibile visualizzare l'argomento richiesto.|
|TopicCorruptedViewOnlineText|\<p > Visualizzatore della guida non è in grado di visualizzare l'argomento richiesto. Potrebbe essersi verificato un errore nel contenuto dell'argomento o in una dipendenza di sistema sottostante.\</p >|
|Funzionalità:|**Controllo Home page**|
|Utilizzare:|Testo che supporta la visualizzazione del contenuto del nodo di livello superiore del Visualizzatore della guida.|
|**Elemento**|**Valore**|
|HomePageTitle|Pagina iniziale del Visualizzatore della Guida|
|HomePageIntroduction|\<p > Benvenuto nel Microsoft Help Viewer, un'origine essenziale di informazioni per tutti gli utenti che utilizzano strumenti, prodotti, tecnologie e servizi Microsoft. Help Viewer consente di accedere alle informazioni di riferimento, al codice di esempio, agli articoli tecnici e altro ancora. Per trovare il contenuto necessario, esplorare il sommario, utilizzare la ricerca full-text o spostarsi nel contenuto utilizzando la parola chiave index.\</p >|
|HomePageContentInstallText|\<p >\<br/> usare la \<una scheda href = "{0}" {1}> Gestisci contenuto\</a > per eseguire le operazioni seguenti:\<UL >\<li > aggiungere contenuto al computer.\</li >\<li > verificare la disponibilità di aggiornamenti per il contenuto locale.\</li >\<li > rimuovere il contenuto dal computer.\</li >\</UL >\</p >|
|HomePageInstalledBooks|Libri installati|
|HomePageNoBooksInstalled|Nessun contenuto trovato nel computer.|
|HomePageHelpSettings|Impostazioni del contenuto della Guida|
|HomePageHelpSettingsText|\<p > l'impostazione corrente è la guida locale. Il Visualizzatore della Guida Visualizza il contenuto installato nel computer.\<br/> per modificare l'origine del contenuto della guida, sulla barra dei menu di Visual Studio scegliere \<span style = "{0}" > Guida, impostare preferenza guida\</span >.\<br/>\</p >|
|MegaByte|MB|

 **personalizzazione. js**

 Il file Branding. js contiene JavaScript usato dagli elementi di personalizzazione del Visualizzatore della Guida di Visual Studio.  Di seguito è riportato un elenco degli elementi di personalizzazione e della funzione JavaScript di supporto.  Tutte le stringhe da localizzare per questo file sono definite nella sezione "stringhe localizzabili" all'inizio del file.  Il file ICL è stato creato per le stringhe loc all'interno del file Branding. js.

||||
|-|-|-|
|**Funzionalità di personalizzazione**|**Funzione JavaScript**|**Descrizione**|
|Var...||Definire le variabili|
|Ottenere il linguaggio del codice utente|setUserPreferenceLang|esegue il mapping di un indice # al linguaggio del codice|
|Impostare e ottenere i valori dei cookie|GetCookie, secookie||
|Membro ereditato|changeMembersLabel|Espandi/Comprimi membro ereditato|
|Quando SelfBranded = false|onLoad|Leggere la stringa di query per verificare se si tratta di una richiesta di stampa.  Impostare tutti i CodeSnippet per concentrare la scheda preferita dell'utente.  Se si tratta di una richiesta di stampa, impostare isPrinterFriendly su true. Verificare la modalità a contrasto elevato.|
|Frammento di codice|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|scrivere tutti gli oggetti controllo comprimibili nell'elenco.|
||CA_Click|in base allo stato dell'area comprimibile, definisce l'immagine e il testo da presentare|
|Contrasto del supporto per il logo|isBlackBackground()|Chiamata eseguita per determinare se lo sfondo è nero.  Accuratezza solo in modalità a contrasto elevato.|
||isHighContrast()|usare un intervallo colorato per rilevare la modalità a contrasto elevato|
||onHighContrast (nero)|Chiamato quando viene rilevato un contrasto elevato|
|Funzionalità LST|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Funzionalità multimediali|didascalia (inizio, fine, testo, stile)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||tosecondi (t)||
||getAllComments(node)||
||styleRectify(styleName, styleValue)||
||showCC (ID)||
||sottotitolo (ID)||

 **FILE HTM**

 Il pacchetto di personalizzazione contiene un set di file HTM che supportano scenari per la comunicazione di informazioni chiave per aiutare gli utenti del contenuto, ad esempio una Home page che contiene una sezione che descrive i set di contenuto installati e le pagine che indicano all'utente quando gli argomenti non possono si trova nel set locale di argomenti. Questi file HTM possono essere modificati per ogni prodotto.  I fornitori di Shell ISO possono utilizzare il pacchetto di personalizzazione predefinito e modificare il comportamento e il contenuto di queste pagine in base alle esigenze.  Questi file fanno riferimento al rispettivo pacchetto di personalizzazione affinché i tag di personalizzazione ottengano il contenuto corrispondente dal file di personalizzazione. XML.

||||
|-|-|-|
|**File**|**Usare**|**Origine contenuto visualizzata**|
|Homepage. htm|Si tratta di una pagina che Visualizza il contenuto attualmente installato e qualsiasi altro messaggio appropriato da presentare all'utente sul contenuto.  Questo file contiene l'attributo meta data aggiuntivo "Microsoft.Help.Id" Content = "-1" che inserisce il contenuto nella parte superiore del sommario del contenuto locale.||
||<META_HOME_PAGE_TITLE_ADD />|Branding. XML, tag \<HomePageTitle >|
||< HOME_PAGE_INTRODUCTION_SECTION_ADD/>|Branding. XML, tag \<HomePageIntroduction >|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding. XML, tag \<HomePageContentInstallText >|
||< HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD/>|Intestazione section branding. XML tag\<HomePageInstalledBooks >, i dati generati dall'applicazione, \<HomePageNoBooksInstalled > quando non è installata alcuna documentazione.|
||< HOME_PAGE_SETTINGS_SECTION_ADD/>|Intestazione section Debranding. XML tag \<HomePageHelpSettings >, Section Text \<HomePageHelpSettingsText >.|
|topiccorrupted. htm|Quando un argomento esiste nel set locale, ma per qualche motivo non è possibile visualizzarlo (contenuto danneggiato).||
||< META_TOPIC_CORRUPTED_TITLE_ADD/>|Branding. XML, tag \<TopicCorruptedTitle >|
||< TOPIC_CORRUPTED_SECTION_ADD/>|Branding. XML, tag \<TopicCorruptedViewOnlineText >|
|topicnotfound. htm|Quando un argomento non viene trovato nel set di contenuto locale, né disponibile online||
||< META_TOPIC_NOT_FOUND_TITLE_ADD/>|Branding. XML, tag \<TopicNotFoundTitle >|
||< META_TOPIC_NOT_FOUND_ID_ADD/>|Branding. XML, tag \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|
||< TOPIC_NOT_FOUND_SECTION_ADD/>|Branding. XML, tag \<TopicNotFoundText >|
|contentnotinstalled.htm|Quando non è installato alcun contenuto locale per il prodotto.||
||< META_CONTENT_NOT_INSTALLED_TITLE_ADD/>|Branding. XML, tag \<ContentNotInstalledTitle >|
||< META_CONTENT_NOT_INSTALLED_ID_ADD/>|Branding. XML, tag \<ContentNotInstalledDownloadContentText >|
||< CONTENT_NOT_INSTALLED_SECTION_ADD/>|Branding. XML, tag \<ContentNotInstalledText >|

 **File CSS**

 Il pacchetto di personalizzazione del Visualizzatore della Guida di Visual Studio contiene due file CSS per supportare la presentazione del contenuto della Guida di Visual Studio coerente:

- Branding. CSS: contiene gli elementi CSS per il rendering in cui SelfBranded = false

- Printer. CSS: contiene gli elementi CSS per il rendering in cui SelfBranded = false

  La personalizzazione dei file CSS include le definizioni per la presentazione degli argomenti di Visual Studio. si noti che il file di personalizzazione. CSS contenuto nell'Branding_\<le impostazioni locali >. mshc dal servizio del pacchetto potrebbe cambiare.

  **File grafici**

  Il contenuto di Visual Studio Visualizza un logo di Visual Studio e altri elementi grafici.  Di seguito è riportato l'elenco completo dei file grafici nel pacchetto di personalizzazione del Visualizzatore della Guida di Visual Studio.

||||
|-|-|-|
|**File**|**Usare**|**Esempi**|
|Cancella. gif|Usato per eseguire il rendering dell'area comprimibile||
|footer_slice.gif|Presentazione del piè di pagina||
|info_icon.gif|Usato per la visualizzazione di informazioni|Dichiarazione di non responsabilità|
|online_icon.gif|Questa icona deve essere associata a collegamenti online||
|tabLeftBD.gif|Usato per eseguire il rendering del contenitore dei frammenti di codice||
|tabRightBD.gif|Usato per eseguire il rendering del contenitore dei frammenti di codice||
|vs_logo_bk.gif|Usato per i riferimenti al logo di contrasto normale come definito nel tag branding. XML \<LogoFileName >.  Per i prodotti Visual Studio, il nome del logo è vs_logo_bk. gif.||
|vs_logo_wh.gif|Usato per i normali riferimenti con logo alto, come definito nel tag di personalizzazione. XML \<LogoFileNameHC >.  Per i prodotti Visual Studio, il nome del logo è vs_logo_wh. gif.||
|ccOff.png|Rappresentazione grafica del didascalia||
|ccOn.png|Rappresentazione grafica del didascalia||
|ImageSprite.png|Usato per eseguire il rendering dell'area comprimibile|immagine espansa o compressa|

### <a name="deploying-a-set-of-topics"></a>Distribuzione di un set di argomenti
 Si tratta di una semplice e rapida esercitazione per la creazione di un set di distribuzione del contenuto del Visualizzatore della Guida costituito da un file MSHA e dal set di CAB o MSHCs contenente gli argomenti. MSHA è un file XML che descrive un set di file CAB o MSHC. Help Viewer può leggere MSHA per ottenere un elenco di contenuti (. CAB o. File MSHC) disponibili per l'installazione locale.

 Si tratta solo di una nozioni di base che descrive la XML Schema di base per il Visualizzatore della Guida MSHA.  Di seguito è riportato un esempio di implementazione di questa breve panoramica e di esempio HelpContentSetup. msha.

 Il nome di MSHA, ai fini di questo nozioni di fondo, è HelpContentSetup. msha (il nome del file può essere qualsiasi elemento, con l'estensione. MSHA). HelpContentSetup. msha (esempio seguente) dovrebbe contenere un elenco dei CAB o MSHCs disponibili.  Il tipo di file deve essere coerente all'interno di MSHA (non supporta una combinazione di MSHA e tipi di file CAB). Per ogni CAB o MSHC deve essere presente un \<div class = "Package" >...\</div > (vedere l'esempio seguente).

 Nota: nell'esempio di implementazione seguente è stato incluso il pacchetto di personalizzazione. Si tratta di un'operazione fondamentale da includere per ottenere gli elementi di rendering del contenuto di Visual Studio necessari e i comportamenti del contenuto.

 File HelpContentSetup. msha di esempio: sostituire "Content set Name 1" e "Content set Name 2" e così via con i nomi file.

```
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

1. Creare una cartella locale, ad esempio "C:\SampleContent"

2. Per questo esempio, si useranno i file MSHC per contenere gli argomenti.  Un MSHC è un file zip con l'estensione del file modificato da. zip a. MSHC.

3. Creare il seguente HelpContentSetup. msha come file di testo. il blocco note è stato usato per creare il file e salvarlo nella cartella indicata sopra (vedere il passaggio 1).

   La classe "personalizzazione" esiste ed è univoca. Il mshc di personalizzazione è incluso in questo nozioni di base, in modo che il contenuto installato avrà la personalizzazione e i comportamenti del contenuto contenuti in MSHCs avranno gli elementi di supporto appropriati contenuti nel pacchetto di personalizzazione. In caso contrario, si verificano errori quando il sistema cerca gli elementi di supporto che non fanno parte del contenuto rippato (installato).

   Per ottenere il pacchetto di personalizzazione di Visual Studio, copiare il file Branding_en-US. mshc in C:\Program Files (x86) \Microsoft Help Viewer\v2.1\ nella cartella di lavoro.

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

 L'uso ed estensione dei passaggi precedenti consentirà a VSPs di distribuire i set di contenuto per il Visualizzatore della Guida di Visual Studio.

### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Aggiunta della guida a Visual Studio Shell (Integrated e isolated)
 **Introduzione**

 Questa procedura dettagliata illustra come incorporare il contenuto della Guida in un'applicazione shell di Visual Studio e quindi distribuirlo.

 **Requisiti**

1. [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]

2. [Visual Studio 2013 Redist della shell isolata](https://aka.ms/VS2013/IsoShell-LP/all)

   **Panoramica**

   Il [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Shell è una versione dell'IDE di [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] in cui è possibile basare un'applicazione. Tali applicazioni contengono la shell isolata insieme alle estensioni create. Usare i modelli di progetto della shell isolata, inclusi nell'SDK [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)], per compilare le estensioni.

   I passaggi di base per la creazione di un'applicazione basata su Shell isolata e la relativa guida:

3. Ottenere il [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] ISO Shell ridistribuibile (un download Microsoft).

4. In Visual Studio creare un'estensione della Guida basata sulla shell isolata, ad esempio l'estensione della Guida contoso descritta più avanti in questa procedura dettagliata.

5. Eseguire il wrapping dell'estensione e della shell ISO ridistribuibile in un file MSI di distribuzione (configurazione di un'applicazione). Questa procedura dettagliata non include un passaggio di configurazione.

   Creare un archivio del contenuto di Visual Studio. Per lo scenario della shell integrata, modificare Visual STUDIO12 con il nome del catalogo del prodotto come indicato di seguito:

- Crea cartella C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12.

- Creare un file denominato CatalogType. XML e aggiungerlo alla cartella. Il file deve contenere le righe di codice seguenti:

  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <catalogType>UserManaged</catalogType>
  ```

  Definire l'archivio del contenuto nel registro di sistema. Per la shell integrata, modificare VisualStudio12 con il nome del catalogo di prodotti:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   Chiave: LocationPath stringa valore: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12\en-US

   Chiave: CatalogName stringa valore: [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] documentazione

  **Creare il progetto**

  Per creare un'estensione della shell isolata:

1. In Visual Studio, in **file**scegliere **nuovo progetto**, in **altri tipi di progetto** scegliere **estendibilità**, quindi scegliere **Visual Studio Shell isolata**. Denominare il progetto `ContosoHelpShell`) per creare un progetto di estendibilità basato sul modello Visual Studio Isolated Shell.

2. In Esplora soluzioni, nella cartella file di risorse del progetto ContosoHelpShellUI aprire ApplicationCommands. vsct. Verificare che questa riga sia impostata come commento (cercare "No_Help"): `<!-- <define name=“No_HelpMenuCommands”/> -->`

3. Premere il tasto F5 per compilare ed eseguire il **debug**. Nell'istanza sperimentale dell'IDE della shell isolata, scegliere il menu **Guida** . Verificare che vengano visualizzati i comandi **Visualizza Guida**, **Aggiungi e Rimuovi contenuto della Guida**e **imposta preferenza** guida.

4. In Esplora soluzioni, nel progetto ContosHelpShell, nella cartella personalizzazione della shell aprire ContosoHelpShell. pkgdef. Per definire il catalogo della Guida di Contoso, aggiungere le righe seguenti:

   ```
    [$RootKey$\Help]
   "Product"="Contoso"
   "Catalog"="Contoso"
   “Version"="100"
   "BrandingPackage"="ContosoBrandingPackage.mshc"
   ```

5. In Esplora soluzioni, nel progetto ContosHelpShell, nella cartella personalizzazione della shell aprire ContosoHelpShell. Application. pkgdef. Per abilitare la Guida sensibile al contesto, aggiungere le righe seguenti:

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

6. In Esplora soluzioni scegliere la voce di menu **Proprietà** dal menu di scelta rapida della soluzione ContosoHelpShell. In **proprietà di configurazione**selezionare **Configuration Manager**. Nella colonna **configurazione** modificare ogni valore di "debug" in "release".

7. Compila la soluzione. Viene creato un set di file in una cartella di versione, che verrà usato nella sezione successiva.

   Per eseguire il test come se venisse distribuito:

8. Nel computer in cui si distribuisce contoso installare la shell ISO scaricata (dalla versione precedente).

9. Creare una cartella in \\\Program Files (x86)\\e denominarla `Contoso`.

10. Copiare il contenuto dalla cartella della versione ContosoHelpShell alla cartella \\\Program Files (x86) \Contoso\

11. Avviare l'editor del registro di sistema scegliendo **Esegui** nel menu **Start** e immettendo `Regedit`. Nell'editor del registro di sistema scegliere **file**, quindi **Importa**. Passare alla cartella del progetto ContosoHelpShell. Nella sottocartella ContosoHelpShell scegliere ContosoHelpShell. reg.

12. Creare un archivio di contenuti:

     Per la shell ISO-creare un archivio del contenuto contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

     Per [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] shell integrata, creare una cartella C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12

13. Creare CatalogType. XML e aggiungere all'archivio del contenuto (passaggio precedente) contenente:

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

14. Aggiungere le chiavi del registro di sistema seguenti:

     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12Key: LocationPath stringa valore:

     Per la shell ISO:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12

     [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] shell integrata:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12en-US

     Chiave: CatalogName stringa valore: [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] documentazione. Per la shell ISO, questo è il nome del catalogo.

15. Copiare il contenuto (CAB o MSHC e MSHA) in una cartella locale.

16. Esempio di riga di comando della shell integrata per il test dell'archivio del contenuto. Per la shell ISO, modificare i valori Catalog e launchingApp in base alle esigenze corrispondenti al prodotto.

      "C:\Programmi (x86) \Microsoft Help Viewer\v2.1\HlpViewer.exe"/catalogName VisualStudio12/helpQuery Method = "Page & ID = ContosoTopic0"/launchingApp Microsoft, VisualStudio, 12.0

17. Avviare l'applicazione Contoso (dalla radice dell'app Contoso). All'interno della shell ISO scegliere la voce **di menu?** e modificare la **preferenza impostare la preferenza** per l'uso della **Guida locale**.

18. All' **interno della shell** , scegliere la voce di menu?, quindi visualizzare la **Guida**. Verrà avviato il Visualizzatore della guida locale. Scegliere la scheda **Gestisci contenuto** . In **origine installazione**scegliere il pulsante di opzione **disco** . Scegliere il pulsante **...** e passare alla cartella locale che contiene il contenuto di Contoso (copiato nella cartella locale nel passaggio precedente). Scegliere HelpContentSetup. msha. Contoso verrà ora visualizzato come libro nelle selezioni del libro. Scegliere **Aggiungi**, quindi fare clic sul pulsante **Aggiorna** (angolo inferiore destro).

19. Nell'IDE di Contoso scegliere il tasto F1 per testare la funzionalità F1.

### <a name="additional-resources"></a>Risorse aggiuntive

Per l'API di runtime, vedere [API della Guida di Windows](https://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).

Per altre informazioni su come sfruttare l'API della guida, vedere [esempi di codice del Visualizzatore della Guida](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Per gli aggiornamenti sui problemi di rilievo, vedere il [file Leggimi del Visualizzatore della Guida](https://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409).