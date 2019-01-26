---
title: Microsoft Help Viewer SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e297493226478c27f3c3eb6d22e45cb5769e42d3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023915"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK

Questo articolo contiene le attività seguenti per gli integratori di Visualizzatore della Guida di Visual Studio:

-   Creazione di un argomento (supporto per F1)

-   Creazione di un pacchetto di contenuto-branding di Help Viewer

-   Distribuzione di un set di articoli

-   Aggiunta della Guida a Visual Studio shell (integrata o isolata)

-   Risorse aggiuntive

### <a name="creating-a-topic-f1-support"></a>Creazione di un argomento (supporto per F1)
In questa sezione viene fornita una panoramica dei componenti di un argomento presentato, requisiti di argomento, una breve descrizione di come creare un argomento (inclusi i requisiti di supporto F1) e, infine, un argomento di esempio con il risultato del rendering.

**Panoramica di argomento del Visualizzatore della Guida**

Quando viene chiamato un argomento per il rendering, il Visualizzatore della Guida ottiene gli elementi del pacchetto di personalizzazione che sono associati all'argomento al momento dell'installazione o l'ultimo aggiornamento, con l'argomento XHTML e combina i due valori per generare la visualizzazione contenuto presentata (personalizzazione di dati + dati dell'argomento).  Il pacchetto del marchio contiene i logo, il supporto di comportamenti del contenuto e il testo branding (copyright, ecc.).  Per altre informazioni sugli elementi del pacchetto del marchio, vedere "Creazione di informazioni personalizzate distintive del Package" di seguito.  Nel caso in cui non è presente alcun pacchetto di personalizzazione associato all'argomento, il Visualizzatore della Guida verrà utilizzato il pacchetto di personalizzazione fallback che si trova nella radice dell'applicazione Help Viewer (Branding_en US.mshc).

**Requisiti di argomento del Visualizzatore**

Per eseguire il rendering correttamente all'interno del visualizzatore Guida in linea, contenuto dell'argomento non elaborato deve essere XHTML 1.1 base di W3C.

In genere, un argomento contiene due sezioni:

-   I metadati (vedere il contenuto di riferimento dei metadati): padre dati sull'argomento, ad esempio, l'ID univoco di argomento, valore della parola chiave, l'argomento del sommario ID, ID del nodo e così via.

-   Corpo del contenuto: conforme a XHTML 1.1 base W3C, che include supportati comportamenti del contenuto (area comprimibile, frammento di codice e così via. Un elenco completo è illustrato di seguito).

Pacchetto di personalizzazione di Visual Studio supportate controlli:

-   Collegamenti

-   CodeSnippet

-   CollapsibleArea

-   Membri ereditati

-   LanguageSpecificText

Stringhe lingua supportate (non maiuscole / minuscole):

-   JavaScript

-   in c# o CSharp

-   cplusplus o Visual c++ o c + +

-   jscript

-   Visual Basic o Visual Basic

-   f # o fsharp o fs

-   altro - una stringa che rappresenta un nome di linguaggio

**Creazione di un argomento di Help Viewer**

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

Successivamente, aggiungere i dati per definire la modalità con cui l'argomento deve essere presentata (propri record con marchio o No), come fare riferimento in questo argomento per F1, in cui è presente in questo argomento nel sommario, il relativo ID (per riferimento al collegamento da altri argomenti), e così via.  Vedere la tabella "Metadati di tale contenuto" di seguito per un elenco completo dei metadati supportati.

-   In questo caso, si userà un pacchetto di personalizzazione, una variante del pacchetto di personalizzazione di Visual Studio Help Viewer.

-   Aggiungere il nome di meta F1 e un valore ("Microsoft.Help.F1" contenuto = "ContosoTopic4") che corrisponderà al valore di F1 fornito nel contenitore delle proprietà IDE.  (Vedere la sezione supporto F1 per ulteriori informazioni).   Si tratta del valore che corrisponde a F1 da chiamare all'interno dell'IDE da visualizzare in questo argomento quando si sceglie il F1 nell'IDE.

-   Aggiungere l'ID dell'argomento. Questa è la stringa che viene utilizzata da altri argomenti per il collegamento a questo argomento.  È l'ID di Visualizzatore della Guida per questo argomento.

-   Per il sommario, aggiungere il nodo padre di questo argomento per definire dove verrà visualizzati in questo nodo del sommario dell'argomento.

-   Per il sommario, aggiungere l'ordine dei nodi di questo argomento. Quando il nodo padre ha un numero n di nodi figlio, definire il percorso di questo argomento nell'ordine dei nodi figlio. Ad esempio, in questo argomento è numero 4 di 4 argomenti figlio.)

Sezione di metadati di esempio:

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

Il corpo (senza includere l'intestazione e piè di pagina) dell'argomento contiene collegamenti della pagina, una sezione di nota, un'area comprimibile, un frammento di codice e una sezione di testo specifico della lingua.  Vedere la sezione della personalizzazione per informazioni su quelle aree dell'argomento presentato.

1.  Aggiungere un tag di titolo argomento:  `<div class="title">Contoso Topic 4</div>`

2.  Aggiungere una sezione di nota: `<div class="alert"> add your table tag and text </div>`

3.  Aggiungere un'area comprimibile:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4.  Aggiungere un frammento di codice:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5.  Aggiungere testo specifico del linguaggio del codice:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Si noti che `devLangnu=` consente di immettere altri linguaggi. Ad esempio, `devLangnu="Fortran"` Visualizza Fortran quando il frammento di codice DisplayLanguage = Fortran

6.  Aggiungere collegamenti della pagina: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
>  Nota: per non supportati nuovi "Lingua di visualizzazione" (esempio, F#, Cobol, Fortran) la colorazione del codice nel frammento di codice sarà bianco e nero.

**Argomento del Visualizzatore della Guida di esempio** il codice viene illustrato come definire i metadati, un frammento di codice, un'area comprimibile e testo specifici della lingua.

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
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**Il tasto F1**

In Visual Studio, selezionare F1 genera i valori forniti dalla posizione del cursore all'interno dell'IDE e popola un "elenco di proprietà" con i valori forniti (basato su posizione del cursore. Quando il cursore è posizionato funzionalità x, funzionalità x è attivo o in stato di attivo e popola l'elenco di proprietà con valori.  Quando si seleziona F1 viene popolato l'elenco di proprietà e il codice di Visual Studio F1 è simile per verificare se l'origine di clienti predefinita della Guida locale oppure online (online è l'impostazione predefinita), quindi crea la stringa appropriata basata sugli utenti impostazione (online è l'impostazione predefinita) - esecuzione della shell (vedere la Guida dell'amministratore per exe parametri di avvio) con i parametri per il Visualizzatore della Guida locale e le parole chiave da contenitore delle proprietà se la Guida locale è il valore predefinito o l'URL di MSDN con la parola chiave nell'elenco dei parametri.

Se vengono restituite tre stringhe per F1, denominato per sotto forma di stringa con più valori, eseguire il primo termine, cercare un riscontro, e se viene trovato, è stata completata; in caso contrario, spostare la stringa successiva.  Ordine è importante. Presentazione delle parole chiave con più valori deve essere più lunga stringa a stringa più breve.  Per effettuare questa verifica nel caso delle parole chiave con più valori, esaminare la stringa URL F1 online, che include la parola chiave scelta.

In Visual Studio 2012, abbiamo messi specificamente a una divisione più forte tra online e offline, in modo che se l'impostazione dell'utente era per Online, quindi viene semplicemente passato la richiesta F1 direttamente al nostro servizio query online su MSDN, anziché il routing tramite l'agente di raccolta della Guida che avevamo in Visual Studio 2010. Abbiamo quindi si basano su uno stato di "contenuto fornitore installato = true" per determinare se eseguire un'operazione diversa in tale contesto. Se true, quindi, viene eseguita questa logica di analisi e il routing a seconda di ciò che si vuole il supporto per i clienti. Se false, quindi è sufficiente passare a MSDN. Se l'impostazione dell'utente è locale, quindi passano tutte le chiamate al motore di Guida locale.

F1 diagramma di flusso:

![Flusso F1](../../extensibility/internals/media/f1flow.png "F1flow")

Quando l'origine del contenuto della Guida predefinito Help Viewer è impostata su online (avvio nel browser):

-   Le funzionalità di Visual Studio Partner (VSP) generano un valore per il contenitore delle proprietà F1 (prefix.keyword contenitore delle proprietà e l'URL in linea per il prefisso trovato nel Registro di sistema): F1 invia un URL VSP + parametri al browser.

-   Funzionalità di Visual Studio (editor di linguaggio, voci di menu specifiche di Visual Studio e così via):  F1 invia un URL di Visual Studio al browser.

Quando l'origine del contenuto della Guida predefinito Help Viewer è impostata su Guida locale (Avvia in Help Viewer):

-   Funzionalità VSP in cui parola chiave corrispondenti tra il contenitore delle proprietà F1 e indice dell'archivio locale (vale a dire il prefix.keyword contenitore delle proprietà = valore trovato nell'indice archivio locale):  F1 esegue il rendering di argomento nel Visualizzatore della Guida.

-   Funzionalità di Visual Studio (alcuna opzione per eseguire l'override di contenitore di proprietà generato dalla funzionalità di Visual Studio VSP): F1 esegue il rendering di un argomento di Visual Studio nel Visualizzatore della Guida.

Impostare i valori del Registro di sistema seguenti per abilitare F1 Fallback per il contenuto della Guida fornitore. Fallback F1 significa che il Visualizzatore della Guida è impostato su cercare F1 Guida contenuti online, e il contenuto del fornitore è installato localmente sul disco rigido degli utenti. Il Visualizzatore della Guida deve esaminare la Guida locale per il contenuto anche se l'impostazione predefinita è per l'assistenza online.

1. Impostare il **VendorContent** valore sotto la chiave del Registro di sistema della Guida 2.3:

   -   Per i sistemi operativi a 32 bit:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:00000001

   -   Per i sistemi operativi a 64 bit:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:00000001

2. Registrare lo spazio dei nomi partner sotto la chiave del Registro di sistema della Guida 2.3:

   - Per i sistemi operativi a 32 bit:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner<em>\\<namespace\></em>

      "località"="offline"

   - Per i sistemi operativi a 64 bit:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<em>\\<namespace\></em>

      "località"="offline"

**Basare l'analisi nativa Namespace**

Per abilitare l'analisi di spazio dei nomi nativo base, aggiungere un nuovo valore DWORD dal nome nel Registro di sistema: BaseNativeNamespaces e impostarne il valore su 1 (sotto la chiave di catalogo che desiderano supportare).  Ad esempio, se si desidera usare il catalogo di Visual Studio, è Impossibile aggiungere la chiave nel percorso:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

Quando una parola chiave F1 nel formato di CHE INTESTAZIONE o di metodi viene rilevato, il carattere '/' verrà analizzato, causando il costrutto seguente:

-   INTESTAZIONE: sarà lo spazio dei nomi che può essere utilizzato per registrare nel Registro di sistema

-   METODO: diventerà la parola chiave che viene passata tramite.

Si consideri ad esempio una libreria personalizzata denominata CustomLibrary e un metodo chiamato MyTestMethod, quando un F1 viene ricevuta richiesta verrà formattato come `CustomLibrary/MyTestMethod`.

Un utente quindi possibile registrare CustomLibrary come lo spazio dei nomi nell'hive partner e fornire qualsiasi chiave hanno l'esigenza di relativa al percorso e la parola chiave passata alla query sarà MyTestMethod.

**Attivare la Guida nell'IDE di strumento di debug**

Aggiungere la seguente chiave del Registro di sistema e il valore:

HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic Help key: Output di Debug visualizzato nel valore delle vendite al dettaglio: SÌ

Nell'IDE, sotto la voce di menu della Guida, selezionare "Debug contesto Guida in linea"

**Contenuto dei metadati**

Nella tabella seguente, qualsiasi stringa che viene visualizzato tra parentesi quadre è un segnaposto che dovrà essere sostituito da un valore riconosciuto. Ad esempio, in \<meta name="Microsoft.Help.Locale" contenuto = "[codice di lingua]" / >, "[codice di lingua]" deve essere sostituito da un valore, ad esempio "en-us".


| Proprietà (rappresentazione HTML) | Descrizione |
| - | - |
| \< meta name="Microsoft.Help.Locale" content="[language-code]" /> | Imposta le impostazioni locali per questo argomento. Se questo tag viene usato in un argomento, deve essere usato una sola volta e deve essere inserito sopra degli altri tag di Microsoft Help. Se non viene utilizzato questo tag, il testo del corpo dell'argomento è indicizzato con word breaker che è associato a impostazioni locali del prodotto, in caso affermativo; in caso contrario, il en-us word breaker viene utilizzato. Questo tag è conforme a RFC 4646 ISOC. Per garantire il corretto funzionamento di Microsoft Help, usare questa proprietà anziché l'attributo Language generale. |
| \< meta name="Microsoft.Help.TopicLocale" content="[language-code]" /> | Imposta le impostazioni locali per questo argomento quando vengono utilizzate anche altre impostazioni locali. Se questo tag viene usato in un argomento, deve essere utilizzata una sola volta. Quando il catalogo contiene contenuto in più lingue, usare questo tag. Negli argomenti di più di un catalogo possono avere lo stesso ID, ma ognuno deve specificare un TopicLocale univoco. L'argomento che specifica un TopicLocale che corrispondono a quelle del catalogo è l'argomento che viene visualizzato nella tabella dei contenuti. Tuttavia, tutte le versioni localizzate dell'argomento vengono visualizzate nei risultati della ricerca. |
| \< TITLE > [Title] \< /title > | Specifica il titolo di questo argomento. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. Se il corpo dell'argomento non contiene un titolo \<div > sezione, questo titolo viene visualizzata nell'argomento e nella tabella dei contenuti. |
| \< meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | Specifica il testo di un collegamento che viene visualizzato nel riquadro dell'indice del Visualizzatore della Guida. Quando si fa clic sul collegamento, viene visualizzato l'argomento. È possibile specificare più parole chiave di indice per un argomento, oppure è possibile omettere questo tag se si preferisce non collegamenti a questo argomento per visualizzati nell'indice. Le parole chiave "K" dalle versioni precedenti della Guida in linea possono essere convertite in questa proprietà. |
| \< meta name="Microsoft.Help.Id" content="[TopicID]"/> | Imposta l'identificatore per questo argomento. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. L'ID deve essere univoco tra gli argomenti nel catalogo con le stesse impostazioni locali. In un altro argomento, è possibile creare un collegamento all'argomento usando questo ID. |
| \< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Specifica la parola chiave F1 per questo argomento. È possibile specificare più parole chiave F1 per un argomento, oppure è possibile omettere questo tag se non si desidera in questo argomento deve essere visualizzato quando un utente dell'applicazione preme F1. In genere, viene specificata solo una parola chiave F1 per un argomento. Le parole chiave "F" dalle versioni precedenti della Guida in linea possono essere convertite in questa proprietà. |
| \< meta name="Description" content="[topic description]" /> | Fornisce una breve descrizione del contenuto in questo argomento. Se questo tag viene usato in un argomento, deve essere utilizzata una sola volta. Questa proprietà è accessibile direttamente dalla libreria di query. non viene archiviato nel file di indice. |
| meta name="Microsoft.Help.TocParent" content="[parent_Id]"/> | Specifica l'argomento principale di questo argomento nel sommario. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. Il valore è Microsoft.Help.Id dell'elemento padre. Un argomento può avere una sola posizione nella tabella dei contenuti. "-1" è considerato l'ID di argomento per la radice del sommario. In [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], tale pagina è home page di Help Viewer. Questo è lo stesso motivo che aggiungiamo specificamente TocParent =-1 per alcuni argomenti per garantire che vengono visualizzati nella parte superiore a livello. Home page di Help Viewer è una pagina di sistema e pertanto non sostituibili. Se un VSP tenta di aggiungere una pagina con l'ID di -1, potrebbe richiedere di essere aggiunti al set di contenuto, ma il Visualizzatore della Guida verrà sempre utilizzata la tabella di sistema - Help Viewer-home page |
| \< meta name="Microsoft.Help.TocOrder" content="[positive integer]"/> | Specifica dove il sommario in questo argomento viene visualizzato nel relativo relativi argomenti di peer. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. Il valore è un numero intero. Un argomento che specifica un valore minore numero intero viene visualizzata sopra un argomento che specifica un valore integer di valore superiore. |
| \< meta name="Microsoft.Help.Product" content="[product code]"/> | Specifica del prodotto descritte in questo argomento. Se questo tag viene usato in un argomento, deve essere utilizzata una sola volta. Queste informazioni possono inoltre essere specificate come un parametro che viene passato all'indicizzatore della Guida. |
| \< meta name="Microsoft.Help.ProductVersion" content="[version number]"/> | Specifica la versione del prodotto descritte in questo argomento. Se questo tag viene usato in un argomento, deve essere utilizzata una sola volta. Queste informazioni possono inoltre essere specificate come un parametro che viene passato all'indicizzatore della Guida. |
| \< meta name="Microsoft.Help.Category" content="[string]"/> | Utilizzato dai prodotti per identificare le sezioni di contenuto. È possibile identificare più sottosezioni per un argomento oppure è possibile omettere questo tag se si desidera evitare che i collegamenti per identificare delle sezioni secondarie. Questo tag viene usato per archiviare gli attributi per TargetOS e TargetFrameworkMoniker quando un argomento viene convertito da una versione precedente della Guida in linea. Il formato del contenuto è AttributeName:AttributeValue. |
| \< contenuto name="Microsoft.Help.TopicVersion META ="[numero versione argomento]"/ > | Specifica la versione dell'argomento quando sono presenti più versioni in un catalogo. Poiché Microsoft.Help.Id non è garantito l'univocità, questo tag è obbligatorio in presenza di più di una versione di un argomento in un catalogo, ad esempio, quando un catalogo contiene un argomento per .NET Framework 3.5 e un argomento per .NET Framework 4 ed entrambi hanno la stessa Micro soft. Help.Id. |
| \< meta name="SelfBranded" content="[TRUE or FALSE]"/> | Specifica se in questo argomento Usa il pacchetto di personalizzazione di gestione librerie della Guida all'avvio o un pacchetto di personalizzazione specifici per l'argomento. Questo tag deve essere TRUE o FALSE. Se è TRUE, il pacchetto di personalizzazione per l'argomento associato sostituisce il pacchetto di personalizzazione che viene impostato quando viene avviata Gestione librerie della Guida in modo che l'argomento viene eseguito il rendering come previsto anche se differisce dal rendering di altro contenuto. Se è FALSE, l'argomento corrente viene eseguito il rendering in base al pacchetto di personalizzazione che viene impostato quando viene avviata Gestione librerie della Guida. Per impostazione predefinita, Gestione librerie della Guida si presuppone self-branding deve essere false, a meno che la variabile SelfBranded è dichiarata come TRUE. Pertanto, non è necessario dichiarare \<nome meta = "SelfBranded" content = "FALSE" / >. |

### <a name="creating-a-branding-package"></a>Creazione di un pacchetto del marchio
La versione di Visual Studio include un numero di diversi prodotti Visual Studio, tra cui la Isolated e shell integrata per partner di Visual Studio.  Ognuno di questi prodotti richiede un certo livello di basate su argomenti di contenuto della Guida di personalizzazione univoche per il prodotto, il supporto.  Negli argomenti di Visual Studio, ad esempio, necessario avere una presentazione del marchio coerenti, mentre SQL Studio, che esegue il wrapping della Shell di ISO, richiede la propria univoco della Guida contenuto della personalizzazione per ogni argomento.  Un Partner Shell integrata può essere opportuno relativi argomenti della Guida per rientrare il principale contenuto della Guida del prodotto Visual Studio, mantenendo le proprie informazioni personalizzate distintive di argomento del.

Personalizzazione dei pacchetti vengono installati per il prodotto che contiene il Visualizzatore della Guida.  Per i prodotti Visual Studio:

-   Un pacchetto di personalizzazione di fallback (Branding_\<delle impostazioni locali >. mshc) viene installato nella directory radice dell'app di Guida Viewer 2.3 (esempio: C:\Programmi\Microsoft file (x86) \Microsoft Help Viewer\v2.3) per il language pack di Help Viewer.  Viene utilizzato per i casi in cui entrambi il prodotto della personalizzazione del pacchetto non è installato (nessun contenuto è stato installato) o in cui il pacchetto di personalizzazione installato è danneggiato.  Gli elementi di Visual Studio (logo e commenti e suggerimenti) vengono ignorati quando viene usato il pacchetto dell'app principale fallback della personalizzazione.

-   Quando il contenuto di Visual Studio viene installato dal servizio di pacchetto di contenuto, viene installato anche un pacchetto del marchio (per il primo scenario di installazione del contenuto di tempo).  Se è presente un aggiornamento per il pacchetto di personalizzazione, l'aggiornamento viene installato quando si verifica il successivo aggiornamento del contenuto o l'azione di installazione del pacchetto aggiuntivi.

Microsoft Help Viewer supporta la personalizzazione degli argomenti in base ai metadati di argomento.

-   In cui i metadati di argomento definiscono self marchio = true, l'argomento è di eseguire il rendering, non eseguire alcuna operazione (per quanto riguarda la personalizzazione).

-   In cui i metadati di argomento definiscono self marchio = false, usare il pacchetto di personalizzazione associato TopicVendor del valore dei metadati.

-   Contenuto in cui i metadati di argomento definiscono name="Microsoft.Help.TopicVendor" =\< nome pacchetto personalizzazione nel fornitore MSHA >, usare il pacchetto di personalizzazione definito nel valore del contenuto.

-   All'interno del catalogo di Visual Studio, è un'applicazione di priorità dei pacchetti di personalizzazione.  Branding predefinito prima Visual Studio viene applicato e quindi, se definiti nei metadati dell'argomento e supportato con le informazioni di personalizzazione associato pacchetto (come definito in msha l'installazione), il fornitore definito personalizzazione viene applicato come una sostituzione.

Elementi di personalizzazione in genere rientrano in tre categorie principali:

-   Elementi di intestazione (esempi includono il collegamento al feedback, responsabilità condizionale, logo)

-   Contenuto dei comportamenti (ad esempio elementi di testo di espansione/compressione controllo e gli elementi di frammento di codice)

-   Elementi di un piè di pagina (ad esempio Copyright)

Gli elementi considerati come gli elementi personalizzati includono (descritti in dettaglio in questa specifica):

-   Logo di catalogo/prodotto (ad esempio, Visual Studio)

-   Elementi link e di posta elettronica di commenti e suggerimenti

-   Dichiarazione di non responsabilità

-   Testo di copyright

I file di supporto nel pacchetto di personalizzazione di Visualizzatore della Guida di Visual Studio includono:

-   Grafica (logo, icone e così via)

-   File di script branding.js - supporti comportamenti del contenuto

-   Branding.XML - le stringhe che vengono usati in modo coerente tra il contenuto del catalogo.  Nota: per gli elementi di testo di localizzazione Visual Studio in branding.xml, includono locid = "\<valore univoco >"

-   Branding.CSS - definizioni di stile per la coerenza di presentazione

-   Printing.CSS - definizioni di stile per la presentazione stampate coerente

Come indicato in precedenza, i pacchetti di personalizzazione sono associati all'argomento:

-   Quando si SelfBranded = false è definita nei metadati, l'argomento eredita il catalogo della personalizzazione del pacchetto

-   O quando SelfBranded = false e vi è un pacchetto di personalizzazione univoche definito nel MSHA e disponibili quando viene installato il contenuto

Per VSPs implementazione di pacchetti della personalizzazione personalizzati (contenuto VSP, SelfBranded = True), per continuare è possibile iniziare con il pacchetto di personalizzazione fallback (installato con il Visualizzatore della Guida) e modificare il nome del file come appropriato.  Il Branding_\<delle impostazioni locali > file mshc è un file zip con l'estensione del file modificato in mshc, pertanto è sufficiente modificare l'estensione da mshc in. zip ed estrarre i contenuti.  Vedere di seguito per la personalizzazione di elementi del pacchetto e modificare come appropriato (ad esempio, modificare il logo per il logo VSP e il riferimento per il logo nel file Branding.xml, aggiornare Branding.xml per specifiche VSP e così via.).

Al termine di tutte le modifiche, creare un file zip contenente gli elementi di personalizzazione desiderati e modificare l'estensione in mshc.

Per associare il pacchetto del marchio personalizzato, creare il MSHA, che contiene il riferimento al file mshc personalizzazione insieme il contenuto mshc (che contiene gli argomenti).  Vedere di seguito "MSHA" per informazioni su come creare una base MSHA.

Il file Branding.xml contiene un elenco di elementi usati per il rendering in modo coerente di elementi specifici in un argomento quando l'argomento contiene \<meta name="Microsoft.Help.SelfBranded" contenuto = "false" / >.  L'elenco di Visual Studio di elementi nel file Branding.xml è riportato di seguito.  Questo elenco deve essere usato quando sono necessari per un modello per adottanti Shell ISO, in cui essi modificare questi elementi (ad esempio logo, commenti e suggerimenti e il Copyright) per soddisfare le proprie marchio del prodotto.

Nota: le variabili indicate da "{n}" sono le dipendenze del codice, rimozione o modifica di questi valori causerà errori ed eventualmente l'arresto anomalo dell'applicazione. Gli identificatori di localizzazione (esempio _locID="codesnippet.n") sono inclusi nel pacchetto di personalizzazione di Visual Studio.

**Branding.xml**


| | |
| - | - |
| Funzionalità: | **CollapsibleArea** |
| Utilizza: | Espandere il testo di controllo del contenuto viene compressa |
| **Elemento** | **Valore** |
| ExpandText | Expand |
| CollapseText | Comprimi |
| Funzionalità: | **CodeSnippet** |
| Utilizza: | Testo del controllo dei frammenti di codice.  Nota: Contenuto frammento di codice con spazio "Non sostanziale" verrà modificato per lo spazio. |
| **Elemento** | **Valore** |
| CopyToClipboard | Copia negli Appunti |
| ViewColorizedText | Visualizza colorati |
| CombinedVBTabDisplayLanguage | Visual Basic (esempio) |
| VBDeclaration | Dichiarazione |
| VBUsage | Utilizzo |
| Funzionalità: | **Commenti e suggerimenti, un piè di pagina e il Logo** |
| Utilizza: | Fornire un controllo di commenti e suggerimenti per il cliente fornire commenti e suggerimenti sull'argomento corrente tramite posta elettronica.  Testo del copyright per il contenuto.  Definizione del logo. |
| **Elemento** | **Valore (queste stringhe possono essere modificate per soddisfare esigenze adopter contenuto).** |
| CopyRight | © 2013 Microsoft Corporation. Tutti i diritti sono riservati. |
| SendFeedback | \<href = "{0}" {1}> Invia commenti e suggerimenti\</a > in questo argomento per Microsoft. |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Funzionalità: | **Dichiarazione di non responsabilità** |
| Utilizza: | Un set di dichiarazioni di non responsabilità specifico per la macchina contenuto tradotto. |
| **Elemento** | **Valore** |
| MT_Editable | Questo articolo è stato tradotto automaticamente. Se si dispone di una connessione a Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità di modifica con il contenuto in lingua inglese originale nello stesso momento. |
| MT_NonEditable | Questo articolo è stato tradotto automaticamente. Se si dispone di una connessione a Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità di modifica con il contenuto in lingua inglese originale nello stesso momento. |
| MT_QualityEditable | Questo articolo è stato tradotto manualmente. Se si dispone di una connessione a Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità di modifica con il contenuto in lingua inglese originale nello stesso momento. |
| MT_QualityNonEditable | Questo articolo è stato tradotto manualmente. Se si dispone di una connessione a Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità di modifica con il contenuto in lingua inglese originale nello stesso momento. |
| MT_BetaContents | Questo articolo è stato tradotto automaticamente per una versione non definitiva. Se si dispone di una connessione a Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità di modifica con il contenuto in lingua inglese originale nello stesso momento. |
| MT_BetaRecycledContents | Questo articolo è stato tradotto manualmente per una versione non definitiva. Se si dispone di una connessione a Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità di modifica con il contenuto in lingua inglese originale nello stesso momento. |
| Funzionalità: | **LinkTable** |
| Utilizza: | Supporto per collegamenti ad argomenti online |
| **Elemento** | **Valore** |
| LinkTableTitle | Tabella dei collegamenti |
| TopicEnuLinkText | Visualizzare la versione inglese\</a > di questo argomento disponibile nel computer. |
| TopicOnlineLinkText | View this topic \<a href="{0}" {1}>online\</a> |
| OnlineText | Online |
| Funzionalità: | **Controllo Audio video** |
| Utilizza: | Visualizzare gli elementi e il testo per il contenuto video |
| **Elemento** | **Valore** |
| MultiMediaNotSupported | Internet Explorer 9 o successiva deve essere installato per supportare {0} contenuto. |
| VideoText | visualizzazione video |
| AudioText | lo streaming di audio |
| OnlineVideoLinkText | \<p > per visualizzare il video associato a questo argomento, fare clic su {0} \<href = "{1}" >{2}qui\</a >.\< / p > |
| OnlineAudioLinkText | \<p > per ascoltare l'audio associato a questo argomento, fare clic su {0} \<href = "{1}" >{2}qui\</a >.\< / p > |
| Funzionalità: | **Controllo contenuto non installato** |
| Utilizza: | Elementi di testo (stringhe) utilizzati per il rendering di contentnotinstalled.htm |
| **Elemento** | **Valore** |
| ContentNotInstalledTitle | Nessun contenuto è stato trovato nel computer. |
| ContentNotInstalledDownloadContentText | \<p > per scaricare il contenuto nel computer \<href = "{0}" {1}> fare clic sulla scheda Gestisci\</a >.\< / p > |
| ContentNotInstalledText | \<p > Nessun contenuto installato nel computer. Consultare l'amministratore per l'installazione del contenuto della Guida locale.  \< /p > |
| Funzionalità: | **Controllo di argomento non trovato** |
| Utilizza: | Elementi di testo (stringhe) utilizzati per il rendering di topicnotfound.htm |
| **Elemento** | **Valore** |
| TopicNotFoundTitle | Impossibile trovare l'argomento richiesto nel computer. |
| TopicNotFoundViewOnlineText | \<p > argomento richiesto non è stato trovato nel computer in uso, ma è possibile \<href = "{0}" {1}> consente di visualizzare l'argomento online\</a >.\< / p > |
| TopicNotFoundDownloadContentText | \<p > vedere il riquadro di spostamento per i collegamenti ad argomenti simili oppure \<href = "{0}" {1}> fare clic sulla scheda Gestisci\</a > per scaricare il contenuto nel computer.\< / p > |
| TopicNotFoundText | \<p > argomento richiesto non è stato trovato nel computer.  \< /p > |
| Funzionalità: | **Argomento danneggiato controllo** |
| Utilizza: | Elementi di testo (stringhe) utilizzati per il rendering di topiccorrupted.htm |
| **Elemento** | **Valore** |
| TopicCorruptedTitle | Impossibile visualizzare l'argomento richiesto. |
| TopicCorruptedViewOnlineText | \<p > Help Viewer non è in grado di visualizzare l'argomento richiesto. Potrebbe esserci un errore nel contenuto dell'argomento o una dipendenza del sistema sottostanti.  \< /p > |
| Funzionalità: | **Controllo pagina iniziale** |
| Utilizza: | Testo che supportano la visualizzazione del contenuto del nodo di primo livello del Visualizzatore della Guida. |
| **Elemento** | **Valore** |
| HomePageTitle | Help Viewer-home page |
| HomePageIntroduction | \<p > Benvenuti in Microsoft Help Viewer, una fonte di informazioni per tutti coloro che usano gli strumenti, prodotti, tecnologie e servizi Microsoft fondamentale. Help Viewer consente di accedere a informazioni di riferimento e sulle procedure, codice di esempio, articoli tecnici e altro ancora. Per trovare il contenuto che è necessario, consultare il sommario, utilizzare la ricerca full-text oppure scorrere il contenuto usando l'indice della parola chiave.  \< /p > |
| HomePageContentInstallText | \<p >\<br / > usare il \<href = "{0}" {1}> Gestisci contenuto\</a > scheda eseguire le operazioni seguenti:\<ul >\<li > aggiungere contenuto al computer in uso.\< / li >\<li > cercare gli aggiornamenti al contenuto in locale.\< / li >\<li > rimuovere contenuto dal computer.\< / li >\</ul > \< /p > |
| HomePageInstalledBooks | Libri installati |
| HomePageNoBooksInstalled | Nessun contenuto è stato trovato nel computer. |
| HomePageHelpSettings | Impostazioni del contenuto della Guida |
| HomePageHelpSettingsText | \<p > il valore impostato corrente è la Guida locale. Help Viewer Visualizza il contenuto installato nel computer. \<br / > per modificare l'origine del contenuto della Guida, nella barra dei menu di Visual Studio, scegliere \<span style = "{0}" > Guida in linea, Imposta preferenza Guida\</span >.\< br / > \< /p > |
| MegaByte | MB |

**branding.js**

Il file branding.js contiene codice JavaScript usato dagli elementi di personalizzazione di Visual Studio Help Viewer.  Di seguito è riportato un elenco degli elementi di personalizzazione e la funzione di supporto JavaScript.  Tutte le stringhe da localizzare per questo file sono definite nella sezione "Stringhe localizzabili" nella parte superiore di questo file.  File ICL è stato creato per le stringhe di percorso all'interno del file branding.js.

||||
|-|-|-|
|**Funzionalità di branding**|**Funzione JavaScript**|**Descrizione**|
|Var...||Definire le variabili|
|Ottenere il linguaggio del codice utente|setUserPreferenceLang|esegue il mapping di un indice & al linguaggio del codice|
|Impostare e ottenere i valori dei cookie|getCookie, setCookie||
|Membri ereditati|changeMembersLabel|Espandi/Comprimi membro ereditato|
|When SelfBranded=False|onLoad|Leggere la stringa di query per verificare se è una richiesta di stampa.  Impostare tutte le codesnippets concentrarsi scheda Preferiti utente.  Se è una richiesta di stampa, quindi impostare isPrinterFriendly su true. Verificare la modalità a contrasto elevato.|
|Frammento di codice|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|scrivere tutti gli oggetti controllo comprimibili in elenco.|
||CA_Click|in base allo stato dell'area comprimibile, definisce quali immagini e testo per presentare|
|Supporto del contrasto per il Logo|isBlackBackground()|Chiamato per determinare se in background è nero.  Solo accurato quando in modalità a contrasto elevato.|
||isHighContrast()|usare un intervallo di colorato per rilevare la modalità a contrasto elevato|
||onHighContrast(black)|Chiamato quando viene rilevato a contrasto elevato|
|Funzionalità LST|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Funzionalità multimediali|Caption (inizio, fine, testo, stile)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(node)||
||styleRectify(styleName, styleValue)||
||showCC(id)||
||SUBTITLE(ID)||

**FILE HTM**

Il pacchetto di personalizzazione contiene un set di file HTM che supportano scenari per la comunicazione di informazioni sulla chiave agli utenti di contenuto della Guida, ad esempio una home page che contiene una sezione che descrive quale set di contenuti installati e le pagine che informa l'utente quando non sono di argomenti Impossibile trovare nel set di argomenti locale. È possibile modificare questi file HTM per ogni prodotto.  I fornitori di Shell ISO sono in grado di eseguire il pacchetto di personalizzazione predefinito e modificare il comportamento e il contenuto di queste pagine a suite loro necessità.  Vedere i rispettivi pacchetti personalizzazione affinché i tag della personalizzazione ottenere il contenuto corrispondente dal file branding.xml questi file.

||||
|-|-|-|
|**File**|**Usare**|**Origine del contenuto visualizzato**|
|homepage.htm|Si tratta di una pagina che consente di visualizzare contenuto attualmente installato e qualsiasi altro messaggio appropriato da presentare all'utente sulla loro contenuto.  Questo file contiene il contenuto aggiuntivo meta data attributo "Microsoft.Help.Id" = "-1" che consente di collocare questo contenuto nella parte superiore del sommario contenuto locale.||
||<META_HOME_PAGE_TITLE_ADD />|Branding.XML, tag \<HomePageTitle >|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|Branding.XML, tag \<HomePageIntroduction >|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.xml, tag \<HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|Titolo sezione tag Branding.xml\<HomePageInstalledBooks >, i dati generati dall'applicazione, \<HomePageNoBooksInstalled > quando non vengono installata nessuna documentazione.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|Titolo sezione tag Branding.xml \<HomePageHelpSettings >, sezione testo \<HomePageHelpSettingsText >.|
|topiccorrupted.htm|Quando un argomento è presente nel set di locale, ma per qualche motivo non può essere visualizzato (contenuto danneggiato).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding.XML, tag \<TopicCorruptedTitle >|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding.xml, tag \<TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Quando un argomento non viene trovato nel contenuto locale impostare, né disponibile online||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.XML, tag \<TopicNotFoundTitle >|
||<META_TOPIC_NOT_FOUND_ID_ADD />|Branding.xml, tag \<TopicNotFoundViewOnlineText> + \<TopicNotFoundDownloadContentText>|
||&LT; TOPIC_NOT_FOUND_SECTION_ADD / &GT;|Branding.XML, tag \<TopicNotFoundText >|
|contentnotinstalled.htm|Quando non è presente contenuto locale per il prodotto installato.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding.XML, tag \<ContentNotInstalledTitle >|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding.xml, tag \<ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|Branding.xml, tag \<ContentNotInstalledText>|

**File CSS**

Il pacchetto Visual Studio Guida Visualizzatore informazioni personalizzate distintive del contiene due file css per supportare la presentazione del contenuto della Guida di Visual Studio coerente:

-   Branding.CSS - contiene gli elementi di css per il rendering where SelfBranded = false

-   Printer.CSS - contiene gli elementi di css per il rendering where SelfBranded = false

File branding.CSS includono le definizioni per la presentazione di Visual Studio argomento (avvertenza è che il branding.css contenuti nel Branding_\<delle impostazioni locali > può cambiare mshc dal servizio pacchetto).

**File di immagine**

Il contenuto di Visual Studio consente di visualizzare un logo di Visual Studio, nonché altri elementi grafici.  Seguito è riportato l'elenco completo dei file di immagine nel pacchetto di personalizzazione di Visual Studio Help Viewer.

||||
|-|-|-|
|**File**|**Usare**|**Esempi**|
|clear.gif|Utilizzato per il rendering Area comprimibile||
|footer_slice.gif|Presentazione di piè di pagina||
|info_icon.gif|Utilizzato quando si visualizzano informazioni|Dichiarazione di non responsabilità|
|online_icon.gif|Questa icona è da associare collegamenti online||
|tabLeftBD.gif|Utilizzato per il rendering del contenitore di frammento di codice||
|tabRightBD.gif|Utilizzato per il rendering del contenitore di frammento di codice||
|vs_logo_bk.gif|Utilizzata per riferimenti di logo contrasto normale, come definito nel tag Branding.xml \<LogoFileName >.  Per i prodotti Visual Studio, nome del logo è vs_logo_bk.gif.||
|vs_logo_wh.gif|Utilizzata per riferimenti normale del logo alto come definito nel tag Branding.xml \<LogoFileNameHC >.  Per i prodotti Visual Studio, nome del logo è vs_logo_wh.gif.||
|ccOff.png|Immagine di sottotitoli codificati||
|ccOn.png|Immagine di sottotitoli codificati||
|ImageSprite.png|Utilizzato per il rendering Area comprimibile|Espandere o comprimere grafico|

### <a name="deploying-a-set-of-topics"></a>Distribuzione di un set di argomenti
Si tratta di un'esercitazione semplice e rapida per la creazione di un set di distribuzione del contenuto di Help Viewer costituito da un file MSHA e il set di file CAB o MSHCs che contiene gli argomenti. Il MSHA è un file XML che descrive un set di file CAB o i file MSHC. Help Viewer può leggere il MSHA per ottenere un elenco di contenuti (il file con estensione File CAB o. File MSHC) disponibili per l'installazione locale.

Questo è solo una panoramica che descrive lo schema XML di base per il MSHA Visualizzatore della Guida.  È un esempio di implementazione seguito in questo esempio HelpContentSetup. msha e breve panoramica.

Il nome del MSHA, ai fini di queste nozioni di base, è HelpContentSetup. msha (il nome del file può essere qualsiasi oggetto, con l'estensione. MSHA). HelpContentSetup. msha (ad esempio riportato di seguito) deve contenere un elenco del file CAB o MSHCs disponibili.  Il tipo di file deve essere coerente all'interno di MSHA (non supporta una combinazione di tipi di file CAB e MSHA). Per ogni file CAB o MSHC, dovrebbe esserci un \<div classe = "pacchetti" >... \</div > (vedere l'esempio riportato di seguito).

Nota: nell'esempio di implementazione seguente, è stato incluso il pacchetto di personalizzazione. Questo è fondamentale da includere per ottenere i necessari elementi di rendering del contenuto di Visual Studio e i comportamenti del contenuto.

File helpcontentsetup. msha di esempio: (Sostituire "nome 1 set di contenuto" e "content set nome 2" e così via con nomi di file.)

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

1.  Creare una cartella locale, ad esempio, "C:\SampleContent"

2.  Per questo esempio, si userà il file MSHC per contenere gli argomenti.  Un MSHC è un file zip con l'estensione del file modificato da ZIP a. MSHC.

3.  Creare il seguente HelpContentSetup. msha come file di testo (blocco note è stato usato per creare il file) e salvarlo nella cartella indicate sopra (vedere il passaggio 1).

La classe "Personalizzazione" esiste ed è univoco. Mshc la personalizzazione è inclusa in queste nozioni di base in modo che il contenuto installato disporrà della personalizzazione, e i comportamenti del contenuto che sono contenuti nel MSHCs avrà gli elementi di supporto appropriato contenuti nel pacchetto del marchio. In caso contrario, si verificheranno degli errori quando il sistema cerca elementi di supporto che non fanno parte di copiati (installato) del contenuto.

Per ottenere il pacchetto di personalizzazione di Visual Studio, copiare file Branding_en US.mshc in C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ cartella di lavoro.

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

Usando ed estendendo i passaggi precedenti abiliterà VSPs distribuire i relativi set di contenuto per il Visualizzatore della Guida di Visual Studio.

### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Aggiunta della Guida a Visual Studio Shell (modalità integrata e isolata)
**Introduzione**

Questa procedura dettagliata illustra come incorporare il contenuto della Guida in un'applicazione di Visual Studio Shell e quindi distribuirlo.

**Requisiti**

1.  [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2.  [Visual Studio 2013 Isolated Shell Redist](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)

**Panoramica**

Il [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell è una versione del [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE in cui è possibile basare un'applicazione. Tali applicazioni contengono della Shell isolata insieme alle estensioni che creano. Usare modelli di progetto Isolated Shell, che sono inclusi nel [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK per compilare estensioni.

I passaggi di base per la creazione di un'applicazione basata su Shell isolata e visualizzarne la Guida:

1. Ottenere il [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ISO Shell redistributable (un download di Microsoft).

2. In Visual Studio, creare un'estensione della Guida basata su Shell isolata, ad esempio, l'estensione della Guida di Contoso che è descritti più avanti in questa procedura dettagliata.

3. Eseguire il wrapping dell'estensione e la Shell di ISO redistributable in una distribuzione MSI (un programma di installazione dell'applicazione). Questa procedura dettagliata non include un passaggio di installazione.

Creare un archivio di contenuto Visual Studio. Per lo scenario Integrated Shell, modificare Studio12 Visual per il nome del catalogo prodotti, come indicato di seguito:

-   Crea cartella C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.

-   Creare un file denominato Catalogtype e aggiungerlo alla cartella. Il file deve contenere le righe di codice seguenti:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Definire l'archivio del contenuto nel Registro di sistema. Per la Shell integrata, modificare il nome del catalogo prodotti VisualStudio15:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

   Legenda: Valore stringa LocationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US

   Legenda: Valore stringa CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Documentazione

**Creare il progetto**

Per creare un'estensione della Shell isolata di:

1.  In Visual Studio, sotto **File**, scegliere **nuovo progetto**, sotto **altri tipi di progetto** Scegli **estendibilità**e quindi scegliere  **Visual Studio Shell isolata**. Denominare il progetto `ContosoHelpShell`) per creare un progetto di estendibilità in base al modello di Visual Studio Isolated Shell.

2.  In Esplora soluzioni aprire ApplicationCommands.vsct nel progetto ContosoHelpShellUI, nella cartella file di risorse. Assicurarsi che questa riga viene impostata come commento (cercare "No_Help"): `<!-- <define name="No_HelpMenuCommands"/> -->`

3.  Premere il tasto F5 per compilare ed eseguire **Debug**. Nell'istanza sperimentale dell'IDE di Shell isolata, scegliere il **aiutare** menu. Assicurarsi che il **Visualizza la Guida**, **Aggiungi e Rimuovi contenuto della Guida**, e **Imposta preferenza Guida** comandi vengono visualizzati.

4.  In Esplora soluzioni aprire ContosoHelpShell.pkgdef nel progetto ContosHelpShell, nella cartella della personalizzazione della Shell. Per definire il catalogo della Guida di Contoso, aggiungere le righe seguenti:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5.  In Esplora soluzioni aprire ContosoHelpShell.Application.pkgdef nel progetto ContosHelpShell, nella cartella della personalizzazione della Shell. Per abilitare la Guida F1, aggiungere le righe seguenti:

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

6.  In Esplora soluzioni, nel menu di scelta rapida della soluzione ContosoHelpShell, scegliere il **proprietà** voce di menu. Sotto **le proprietà di configurazione**, selezionare **Configuration Manager**. Nel **configurazione** colonna, modificare ogni valore di "Debug" in "Release".

7.  Compilare la soluzione. Consente di creare un set di file in una cartella di rilascio, che verrà usata nella sezione successiva.

Per testare questo come se distribuita:

1. Nel computer si stanno distribuendo Contoso per installare il file da Shell ISO (sopra).

2. Creare una cartella nel \\\Programmi file (x86)\\e denominarla `Contoso`.

3. Copiare il contenuto dalla cartella di rilascio ContosoHelpShell a \\(x86) \Contoso\ cartella \Programmi.

4. Avviare l'Editor del Registro di sistema scegliendo **eseguiti** nel **avviare** menu e immettendo `Regedit`. Nell'editor del Registro di sistema, scegli **File**e quindi **importazione**. Passare alla cartella del progetto ContosoHelpShell. Nella sottocartella ContosoHelpShell, scegliere ContosoHelpShell.reg.

5. Creare un archivio del contenuto:

    Per la Shell ISO - creare un archivio del contenuto Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

    Per [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Integrated Shell, creare cartelle C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15

6. Creare Catalogtype e aggiungere l'archivio del contenuto (passaggio precedente) che contiene:

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Aggiungere le chiavi del Registro di sistema seguenti:

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: Valore stringa LocationPath:

    Per ISO Shell:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell integrata:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Legenda: Valore stringa CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Documentazione. Per ISO Shell, si tratta del nome del catalogo.

8. Copiare il contenuto (file CAB o MSHC e MSHA) in una cartella locale.

9. Esempio riga di comando di Shell integrata per il test dell'archivio del contenuto. Per ISO Shell, modificare i valori di catalogo e launchingApp come appropriato in base al prodotto.

     "C:\Programmi\Microsoft file (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe" /catalogName VisualStudio15 /helpQuery metodo = "pagina & id = ContosoTopic0" /launchingApp Microsoft, Visual Studio, 12.0

10. Avviare l'applicazione Contoso (dalla radice dell'app di Contoso). All'interno della Shell di ISO, scegliere il **aiutare** voce di menu e modifica il **Imposta preferenza Guida** al **utilizza Guida locale**.

11. All'interno della shell, scegliere il **aiutare** voce di menu, quindi **Visualizza Guida**. Deve essere avviato il Visualizzatore della Guida locale. Scegliere la scheda **Gestisci contenuto**. Sotto **origine dell'installazione**, scegliere il **disco** pulsante di opzione. Scegliere il **...**  pulsante e passare alla cartella locale contenente il contenuto di Contoso (copiato nella cartella locale nel passaggio precedente). Scegliere il HelpContentSetup. msha. Contoso verranno ora visualizzati sotto forma di libro nelle selezioni delle libro. Scegliere **Add**, quindi scegliere il **Update** pulsante (nell'angolo inferiore destro).

12. All'interno dell'IDE di Contoso, premere il tasto F1 per testare la funzionalità F1.

### <a name="additional-resources"></a>Risorse aggiuntive

Per le API di Runtime, vedere [API di Windows della Guida](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Per altre informazioni su come usare l'API della Guida, vedere [esempi di codice di Help Viewer](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

È possibile inviare suggerimenti sulle funzionalità nella [Community degli sviluppatori](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).