---
title: Microsoft Help Viewer SDK | Microsoft Docs
description: Informazioni sulle Visual Studio help viewer, ad esempio la creazione di un articolo, la creazione di un pacchetto di personalizzazione del contenuto di Help Viewer e la distribuzione di un set di articoli.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8bc2ed473e25dc75d0155bc864aa02c157e3482f
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448324"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK

Questo articolo contiene le attività seguenti per gli integratori Visual Studio Help Viewer:

- Creazione di un argomento (supporto F1)

- Creazione di un pacchetto di personalizzazione del contenuto di Help Viewer

- Distribuzione di un set di articoli

- Aggiunta della Guida alla shell Visual Studio (integrata o isolata)

- Risorse aggiuntive

## <a name="create-a-topic-f1-support"></a>Creare un argomento (supporto F1)

Questa sezione offre una panoramica dei componenti di un argomento presentato, i requisiti dell'argomento, una breve descrizione di come creare un argomento (inclusi i requisiti di supporto F1) e infine un argomento di esempio con il risultato di cui è stato eseguito il rendering.

**Panoramica dell'argomento di Help Viewer**

Quando viene chiamato un argomento per il rendering, Help Viewer ottiene gli elementi del pacchetto di personalizzazione associati all'argomento al momento dell'installazione o dell'ultimo aggiornamento, insieme all'argomento XHTML, e combina i due elementi per ottenere la visualizzazione contenuto presentata (dati di personalizzazione e dati dell'argomento).  Il pacchetto di personalizzazione contiene logo, supporto per i comportamenti del contenuto e testo personalizzato (copyright e così via).  Per altre informazioni sugli elementi del pacchetto di personalizzazione, vedere "Creazione di un pacchetto di personalizzazione" di seguito.  Se all'argomento non è associato alcun pacchetto di personalizzazione, Help Viewer userà il pacchetto di personalizzazione di fallback disponibile nella radice dell'applicazione Help Viewer (Branding_en-US.mshc).

**Requisiti degli argomenti di Help Viewer**

Per eseguire correttamente il rendering all'interno di Help Viewer, il contenuto dell'argomento non elaborato deve essere XHTML W3C Basic 1.1.

Un argomento contiene in genere due sezioni:

- Metadati (vedere Informazioni di riferimento sui metadati del contenuto): dati sull'argomento, ad esempio l'ID univoco dell'argomento, il valore della parola chiave, l'ID del sommario dell'argomento, l'ID nodo padre e così via.

- Contenuto del corpo: conforme a W3C Basic 1.1 XHTML, che include i comportamenti del contenuto supportati (area comprimibile, frammento di codice e così via. Di seguito è riportato un elenco completo.

Visual Studio controlli supportati per il pacchetto di personalizzazione:

- Collegamenti

- CodeSnippet

- Area comprimibile

- Membro ereditato

- LanguageSpecificText

Stringhe di lingua supportate (senza distinzione tra maiuscole e minuscole):

- JavaScript

- csharp o c #

- cplusplus o visualc++ o c++

- jscript

- visualbasic o vb

- f# o fsharp o fs

- other: stringa che rappresenta un nome di lingua

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

Aggiungere quindi i dati per definire la modalità di presentazione dell'argomento (auto-personalizzazione o meno), come fare riferimento a questo argomento per F1, dove questo argomento è presente all'interno del sommario, il relativo ID (per informazioni di riferimento sui collegamenti da altri argomenti) e così via. Per un elenco completo dei metadati supportati, vedere la tabella "Metadati del contenuto" riportata di seguito.

- In questo caso, si userà il pacchetto di personalizzazione, una variante del pacchetto di personalizzazione Visual Studio Help Viewer.

- Aggiungere il metanomo F1 e il valore ("Microsoft.Help.F1" content=" ContosoTopic4") che corrisponderà al valore F1 fornito nel contenitore delle proprietà ide. Per altre informazioni, vedere la sezione Supporto F1. Si tratta del valore corrispondente alla chiamata F1 dall'interno dell'IDE per visualizzare questo argomento quando si sceglie F1 nell'IDE.

- Aggiungere l'ID argomento. Si tratta della stringa utilizzata da altri argomenti per il collegamento a questo argomento. È l'ID visualizzatore della Guida per questo argomento.

- Per il sommario, aggiungere il nodo padre di questo argomento per definire dove verrà visualizzato il nodo del sommario di questo argomento.

- Per il sommario, aggiungere l'ordine dei nodi di questo argomento. Quando il nodo padre ha `n` un numero di nodi figlio, definire nell'ordine dei nodi figlio la posizione di questo argomento. Ad esempio, questo argomento è il numero 4 di 4 argomenti figlio.

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

Il corpo (senza l'intestazione e il piè di pagina) dell'argomento conterrà collegamenti di pagina, una sezione nota, un'area comprimibile, un frammento di codice e una sezione di testo specifico del linguaggio.  Per informazioni su queste aree dell'argomento presentato, vedere la sezione relativa alla personalizzazione.

1. Aggiungere un tag del titolo dell'argomento:  `<div class="title">Contoso Topic 4</div>`

2. Aggiungere una sezione note: `<div class="alert"> add your table tag and text </div>`

3. Aggiungere un'area comprimibile:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Aggiungere un frammento di codice:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Aggiungere testo specifico della lingua del codice:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` si noti che consente di immettere altre `devLangnu=` lingue. Ad esempio, `devLangnu="Fortran"` visualizzaMplran quando il frammento di codice DisplayLanguage = Fortran

6. Aggiungere collegamenti di pagina: `<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Nota: per la nuova colorazione del codice "Lingua di visualizzazione" non supportata (ad esempio, F#, Cobol, Fortran) nel frammento di codice sarà monocromatica.

**Argomento visualizzatore della Guida di esempio** Il codice illustra come definire metadati, un frammento di codice, un'area comprimibile e testo specifico del linguaggio.

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

In Visual Studio F1 genera i valori forniti dalla posizione del cursore all'interno dell'IDE e popola un "contenitore delle proprietà" con i valori forniti (in base alla posizione del cursore. Quando il cursore si trova sulla funzionalità x, la funzionalità x è attiva/attiva e popola il contenitore delle proprietà con valori.  Quando si seleziona F1, il contenitore delle proprietà viene popolato e il codice Visual Studio F1 verifica se l'origine della Guida predefinita dei clienti è locale o online (l'impostazione predefinita è online), quindi crea la stringa appropriata in base all'impostazione degli utenti (online è l'impostazione predefinita) - esecuzione della shell (vedere guida dell'amministratore della Guida per i parametri di avvio exe) con parametri per il visualizzatore della Guida locale + parole chiave dal contenitore delle proprietà se la Guida locale è l'impostazione predefinita o l'URL MSDN con la parola chiave nell'elenco di parametri.

Se vengono restituite tre stringhe per F1, definite stringa multivalore, prendere il primo termine, cercare un hit e, se viene trovato, è stato fatto; In caso contrario, passare alla stringa successiva.  L'ordine è importante. La presentazione delle parole chiave multivalore deve essere la stringa più lunga alla stringa più breve.  Per verificarlo nel caso di parole chiave multivalore, esaminare la stringa url F1 online, che includerà la parola chiave scelta.

Nel Visual Studio 2012 è stata intenzionalmente definita una divisione più forte tra online e offline, in modo che se l'impostazione dell'utente fosse online, la richiesta F1 è stata semplicemente passata direttamente al servizio di query online su MSDN anziché eseguire il routing tramite l'agente della libreria della Guida di Visual Studio 2010. Si fa quindi affidamento su uno stato di "contenuto del fornitore installato = true" per determinare se eseguire un'operazione diversa in tale contesto. Se true, questa logica di analisi e routing viene quindi eseguita in base a ciò che si vuole supportare per i clienti. Se false, è sufficiente passare a MSDN. Se l'impostazione dell'utente è Locale, tutte le chiamate passano al motore della Guida locale.

Diagramma di flusso F1:

![Flusso F1](../../extensibility/internals/media/f1flow.png "F1flow")

Quando l'origine del contenuto della Guida predefinita di Help Viewer è impostata su online (Avvia nel browser):

- le funzionalità di Visual Studio Partner (VSP) generano un valore nel contenitore delle proprietà F1 (property bag prefix.keyword e URL online per il prefisso trovato nel Registro di sistema): F1 invia un URL VSP+ parametri al browser.

- Visual Studio funzionalità (editor di linguaggio, Visual Studio voci di menu specifiche e così via): F1 invia un URL Visual Studio al browser.

Quando l'origine del contenuto della Guida predefinita di Help Viewer è impostata su Guida locale (Avvia in Help Viewer):

- Funzionalità vsp in cui la parola chiave corrisponde tra il contenitore delle proprietà F1 e l'indice dell'archivio locale (ovvero, il contenitore delle proprietà prefix.keyword = il valore presente nell'indice dell'archivio locale): F1 esegue il rendering dell'argomento in Help Viewer.

- Visual Studio funzionalità (nessuna opzione che consente a VSP di eseguire l'override del contenitore delle proprietà generato dalle funzionalità di Visual Studio): F1 esegue il rendering di un argomento Visual Studio in Help Viewer.

Impostare i valori del Registro di sistema seguenti per abilitare il fallback F1 per il contenuto della Guida del fornitore. F1 Fallback significa che Help Viewer è impostato per cercare il contenuto della Guida in linea di F1 e il contenuto del fornitore viene installato localmente nel disco rigido degli utenti. Help Viewer dovrebbe esaminare la Guida locale per il contenuto anche se l'impostazione predefinita è per la Guida online.

1. Impostare il **valore VendorContent** nella chiave del Registro di sistema Help 2.3:

   - Per i sistemi operativi a 32 bit:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:00000001

   - Per i sistemi operativi a 64 bit:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:00000001

2. Registrare lo spazio dei nomi del partner nella chiave del Registro di sistema Della Guida 2.3:

   - Per i sistemi operativi a 32 bit:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner<<em> \\ spazio dei nomi \> </em>

      "location"="offline"

   - Per i sistemi operativi a 64 bit:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<<em> \\ spazio dei nomi \> </em>

      "location"="offline"

**Analisi dello spazio dei nomi nativo di base**

Per attivare l'analisi dello spazio dei nomi nativo di base, nel Registro di sistema aggiungere un nuovo valore DWORD con il nome BaseNativeNamespaces e impostarne il valore su 1 (sotto la chiave del catalogo che si vuole supportare).  Ad esempio, se si vuole usare il Visual Studio, è possibile aggiungere la chiave al percorso:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

Quando viene rilevata una parola chiave F1 nel formato HEADER/METHOD, il carattere '/' viene analizzato, con il risultato del costrutto seguente:

- HEADER: sarà lo spazio dei nomi che può essere usato per la registrazione nel Registro di sistema

- METHOD: diventerà la parola chiave che viene passata.

Ad esempio, data una libreria personalizzata denominata CustomLibrary e un metodo denominato MyTestMethod, quando viene inviata una richiesta F1 verrà formattata come `CustomLibrary/MyTestMethod` .

Un utente può quindi registrare CustomLibrary come spazio dei nomi nell'hive Partners e specificare la chiave di posizione desiderata e la parola chiave passata alla query sarà MyTestMethod.

**Abilitare lo strumento di debug della Guida nell'IDE**

Aggiungere la chiave e il valore del Registro di sistema seguenti:

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic Help**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Dynamic Help**

::: moniker-end

Valore: Visualizza output di debug nei dati delle vendite al dettaglio: SÌ

Nell'IDE, sotto la voce di menu ? selezionare **Debug Help Context (Debug contesto Guida).**

**Metadati del contenuto**

Nella tabella seguente qualsiasi stringa visualizzata tra parentesi quadre è un segnaposto che deve essere sostituito da un valore riconosciuto. In , ad \<meta name="Microsoft.Help.Locale" content="[language code]" /> esempio, "[language code]" deve essere sostituito da un valore come "en-us".

| Proprietà (rappresentazione HTML) | Descrizione |
| - | - |
| \< meta name="Microsoft.Help.Locale" content="[language-code]" /> | Imposta le impostazioni locali per questo argomento. Se questo tag viene usato in un argomento, deve essere usato una sola volta e deve essere inserito sopra qualsiasi altro tag della Guida Microsoft. Se questo tag non viene usato, il testo del corpo dell'argomento viene indicizzato usando il word breaker associato alle impostazioni locali del prodotto, se specificato; In caso contrario, viene usato il word breaker en-us. Questo tag è conforme a ISOC RFC 4646. Per garantire il corretto funzionamento della Guida Microsoft, usare questa proprietà anziché l'attributo Language generale. |
| \< meta name="Microsoft.Help.TopicLocale" content="[language-code]" /> | Imposta le impostazioni locali per questo argomento quando vengono usate anche altre impostazioni locali. Se questo tag viene usato in un argomento, deve essere usato una sola volta. Usare questo tag quando il catalogo contiene contenuto in più lingue. Più argomenti in un catalogo possono avere lo stesso ID, ma ognuno deve specificare un elemento TopicLocale univoco. L'argomento che specifica un argomento TopicLocale che corrisponde alle impostazioni locali del catalogo è l'argomento visualizzato nel sommario. Tuttavia, tutte le versioni linguistiche dell'argomento vengono visualizzate nei risultati della ricerca. |
| \< title>[Titolo]\</title> | Specifica il titolo di questo argomento. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. Se il corpo dell'argomento non contiene una sezione del titolo, questo titolo viene visualizzato nell'argomento e \<div> nel sommario. |
| \< meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | Specifica il testo di un collegamento visualizzato nel riquadro dell'indice di Help Viewer. Quando si fa clic sul collegamento, viene visualizzato l'argomento. È possibile specificare più parole chiave di indice per un argomento oppure omettere questo tag se non si desidera che i collegamenti a questo argomento vengano visualizzati nell'indice. Le parole chiave "K" delle versioni precedenti della Guida possono essere convertite in questa proprietà. |
| \< meta name="Microsoft.Help.Id" content="[TopicID]"/> | Imposta l'identificatore per questo argomento. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. L'ID deve essere univoco tra gli argomenti del catalogo con le stesse impostazioni locali. In un altro argomento è possibile creare un collegamento a questo argomento usando questo ID. |
| \< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Specifica la parola chiave F1 per questo argomento. È possibile specificare più parole chiave F1 per un argomento oppure omettere questo tag se non si vuole che questo argomento sia visualizzato quando un utente dell'applicazione preme F1. In genere, viene specificata una sola parola chiave F1 per un argomento. Le parole chiave "F" delle versioni precedenti della Guida possono essere convertite in questa proprietà. |
| \< meta name="Description" content="[topic description]" /> | Fornisce un breve riepilogo del contenuto di questo argomento. Se questo tag viene usato in un argomento, deve essere usato una sola volta. Questa proprietà è accessibile direttamente dalla libreria di query. non è archiviato nel file di indice. |
| meta name="Microsoft.Help.TocParent" content="[parent_Id]"/> | Specifica l'argomento padre di questo argomento nel sommario. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. Il valore è il Microsoft.Help.Id dell'elemento padre. Un argomento può avere una sola posizione nel sommario. "-1" è considerato l'ID argomento per la radice del sommario. In [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] tale pagina è help viewer home page. Questo è lo stesso motivo per cui tocParent=-1 viene aggiunto ad alcuni argomenti per assicurarsi che siano visualizzati al livello superiore. Help Viewer home page è una pagina di sistema e quindi non sostituibile. Se un vsp tenta di aggiungere una pagina con ID -1, potrebbe essere aggiunta al set di contenuto, ma Help Viewer userà sempre la pagina di sistema - Home page di Help Viewer |
| \< meta name="Microsoft.Help.TocOrder" content="[positive integer]"/> | Specifica dove viene visualizzato questo argomento nel sommario in relazione ai relativi argomenti peer. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. Il valore è un numero intero. Un argomento che specifica un numero intero di valore inferiore viene visualizzato sopra un argomento che specifica un numero intero di valore superiore. |
| \< meta name="Microsoft.Help.Product" content="[product code]"/> | Specifica il prodotto descritto in questo argomento. Se questo tag viene usato in un argomento, deve essere usato una sola volta. Queste informazioni possono essere fornite anche come parametro passato all'indicizzatore della Guida. |
| \< meta name="Microsoft.Help.ProductVersion" content="[version number]"/> | Specifica la versione del prodotto descritta in questo argomento. Se questo tag viene usato in un argomento, deve essere usato una sola volta. Queste informazioni possono essere fornite anche come parametro passato all'indicizzatore della Guida. |
| \< meta name="Microsoft.Help.Category" content="[string]"/> | Usato dai prodotti per identificare le sottosezioni del contenuto. È possibile identificare più sottosezioni per un argomento oppure omettere questo tag se non si desidera che i collegamenti identififino le sottosezioni. Questo tag viene usato per archiviare gli attributi per TargetOS e TargetFrameworkMoniker quando un argomento viene convertito da una versione precedente della Guida. Il formato del contenuto è AttributeName:AttributeValue. |
| \< meta name="Microsoft.Help.TopicVersion content="[topic version number]"/> | Specifica questa versione dell'argomento quando in un catalogo sono presenti più versioni. Poiché Microsoft.Help.Id non è garantito come univoco, questo tag è obbligatorio quando in un catalogo sono presenti più versioni di un argomento, ad esempio quando un catalogo contiene un argomento per .NET Framework 3.5 e un argomento per .NET Framework 4 ed entrambi hanno lo stesso Microsoft.Help.Id. |
| \< meta name="SelfBranded" content="[TRUE or FALSE]"/> | Specifica se in questo argomento viene utilizzato il pacchetto di personalizzazione di avvio di Gestione librerie della Guida o un pacchetto di personalizzazione specifico dell'argomento. Questo tag deve essere TRUE o FALSE. Se è TRUE, il pacchetto di personalizzazione per l'argomento associato esegue l'override del pacchetto di personalizzazione impostato all'avvio di Gestione librerie della Guida in modo che il rendering dell'argomento sia previsto anche se differisce dal rendering di altro contenuto. Se è FALSE, viene eseguito il rendering dell'argomento corrente in base al pacchetto di personalizzazione impostato all'avvio di Gestione librerie della Guida. Per impostazione predefinita, Gestione librerie della Guida presuppone che l'auto-personalizzazione sia false, a meno che la variabile SelfBranded non sia dichiarata come TRUE. Pertanto, non è necessario dichiarare \<meta name="SelfBranded" content="FALSE"/> . |

## <a name="create-a-branding-package"></a>Creare un pacchetto di personalizzazione

La Visual Studio include diversi prodotti Visual Studio, tra cui shell isolate e integrate per Visual Studio partner.  Ognuno di questi prodotti richiede un certo livello di supporto per la personalizzazione del contenuto della Guida basato su argomenti, univoco per il prodotto.  Ad esempio, Visual Studio deve avere una presentazione coerente del marchio, mentre SQL Studio, che esegue il wrapping di ISO Shell, richiede una personalizzazione univoca del contenuto della Guida per ogni argomento.  Un partner shell integrato potrebbe volere che gli argomenti della Guida siano inclusi nel contenuto della Guida Visual Studio prodotto, mantenendo al tempo stesso la personalizzazione degli argomenti.

I pacchetti di personalizzazione vengono installati dal prodotto contenente Help Viewer.  Per Visual Studio seguenti:

- Un pacchetto di personalizzazione di fallback (Branding_ .mshc) viene installato nella radice \<locale> dell'app Help Viewer 2.3 (ad esempio: C:\Programmi (x86)\Microsoft Help Viewer\v2.3) dal language pack.  Viene usato per i casi in cui il pacchetto di personalizzazione del prodotto non è installato (non è stato installato alcun contenuto) o in cui il pacchetto di personalizzazione installato è danneggiato.  Gli Visual Studio (logo e commenti) vengono ignorati quando viene usato il pacchetto di personalizzazione di fallback della radice dell'app.

- Quando Visual Studio contenuto viene installato dal servizio del pacchetto di contenuto, viene installato anche un pacchetto di personalizzazione (per la prima volta scenario di installazione del contenuto).  Se è presente un aggiornamento del pacchetto di personalizzazione, l'aggiornamento viene installato quando si verifica il successivo aggiornamento del contenuto o l'azione di installazione del pacchetto aggiuntiva.

Il Microsoft Help Viewer supporta la personalizzazione degli argomenti in base ai metadati dell'argomento.

- Dove i metadati dell'argomento definiscono auto-personalizzazione = true, eseguire il rendering dell'argomento così come sono, non eseguire alcuna operazione (per quanto riguarda la personalizzazione).

- Se i metadati dell'argomento definiscono self-branded = false, usare il pacchetto di personalizzazione associato al valore dei metadati TopicVendor.

- Dove i metadati dell'argomento definiscono name="Microsoft.Help.TopicVendor" content= , usare il pacchetto di personalizzazione \< branding package name in vendor MSHA> definito nel valore del contenuto.

- All'interno Visual Studio, è disponibile un'applicazione prioritaria di pacchetti di personalizzazione.  Prima Visual Studio viene applicata la personalizzazione predefinita e quindi, se definita nei metadati dell'argomento e supportata con il pacchetto di personalizzazione associato (come definito nel msha di installazione), la personalizzazione definita dal fornitore viene applicata come sostituzione.

Gli elementi di personalizzazione rientrano in genere in tre categorie principali:

- Elementi di intestazione (esempi includono collegamento per commenti e suggerimenti, testo della dichiarazione di non responsabilità condizionale, logo)

- Comportamenti del contenuto (esempi includono elementi di testo del controllo expand/collapse ed elementi del frammento di codice)

- Elementi piè di pagina (esempio Copyright)

Gli elementi considerati come elementi personalizzati includono (in dettaglio in questa specifica):

- Logo catalogo/prodotto (ad esempio, Visual Studio)

- Collegamento di commenti e suggerimenti ed elementi di posta elettronica

- Testo della clausola di responsabilità

- Testo sul copyright

I file di supporto nel pacchetto di personalizzazione Visual Studio Help Viewer includono:

- Grafica (logo, icone e così via)

- Branding.js: file script che supportano i comportamenti del contenuto

- Branding.xml: stringhe usate in modo coerente nel contenuto del catalogo.  Nota: per Visual Studio di testo di localizzazione nel branding.xml, includere _locID=" \<unique value> "

- Branding.css: definizioni di stile per la coerenza della presentazione

- Printing.css: definizioni di stile per una presentazione stampata coerente

Come indicato in precedenza, i pacchetti di personalizzazione sono associati all'argomento:

- Quando SelfBranded = false è definito nei metadati, l'argomento eredita il pacchetto di personalizzazione del catalogo

- Oppure quando SelfBranded = false ed è presente un pacchetto di personalizzazione univoco definito in MSHA e disponibile quando il contenuto viene installato

Per i vsp che implementano pacchetti di personalizzazione personalizzati (contenuto VSP, SelfBranded=True), un modo per procedere è iniziare con il pacchetto di personalizzazione di fallback (installato con Help Viewer) e modificare il nome del file in base alle esigenze.  Il file Branding_ con estensione mshc è un file ZIP con estensione mshc, quindi è sufficiente modificare l'estensione da mshc a .zip ed estrarre il \<locale> contenuto.  Vedere di seguito per informazioni sulla personalizzazione degli elementi del pacchetto e modificare in base alle esigenze (ad esempio, modificare il logo con il logo VSP e il riferimento al logo nel file di Branding.xml, aggiornare Branding.xml in base alle specifiche vsp e così via).

Dopo aver apportato tutte le modifiche, creare un file ZIP contenente gli elementi di personalizzazione desiderati e modificare l'estensione in .mshc.

Per associare il pacchetto di personalizzazione, creare MSHA, che contiene il riferimento al file mshc di personalizzazione insieme al contenuto mshc (contenente gli argomenti).  Vedere di seguito "MSHA" per informazioni su come creare una MSHA di base.

Il file Branding.xml contiene un elenco di elementi usati per il rendering coerente di elementi specifici in un argomento quando l'argomento contiene \<meta name="Microsoft.Help.SelfBranded" content="false"/> .  Di Visual Studio l'elenco di Branding.xml di elementi nel file di configurazione.  Questo elenco è destinato a essere usato come modello per gli utenti della shell ISO, in cui modificano questi elementi (ad esempio logo, feedback e copyright) per soddisfare le proprie esigenze di personalizzazione del prodotto.

Nota: le variabili notate da "{n}" hanno dipendenze dal codice. La rimozione o la modifica di questi valori causerà errori ed eventualmente un arresto anomalo dell'applicazione. Gli identificatori di localizzazione (_locID="codesnippet.n") sono inclusi nel pacchetto Visual Studio personalizzazione.

**Branding.xml**

| Elemento | Descrizione |
| - | - |
| Funzionalità: | **Area comprimibile** |
| Usare: | Espandi comprime il testo del controllo contenuto |
| **elemento** | **Valore** |
| ExpandText | Espandere |
| CollapseText | Comprimi |
| Funzionalità: | **CodeSnippet** |
| Usare: | Testo del controllo del frammento di codice.  Nota: il contenuto del frammento di codice con spazio "Non di rilievo" verrà modificato in spazio. |
| **elemento** | **Valore** |
| CopyToClipboard | Copia negli Appunti |
| ViewColorizedText | Visualizzazione colorata |
| CombinedVBTabDisplayLanguage | Visual Basic (esempio) |
| VBDeclaration | Dichiarazione |
| VBUsage | Utilizzo |
| Funzionalità: | **Commenti, piè di pagina e logo** |
| Usare: | Fornire un controllo feedback per consentire al cliente di fornire commenti e suggerimenti sull'argomento corrente tramite posta elettronica.  Testo del copyright per il contenuto.  Definizione del logo. |
| **elemento** | **Valore (queste stringhe possono essere modificate in base alle esigenze dell'utente che adotta il contenuto).** |
| Copyright | © 2013 Microsoft Corporation. Tutti i diritti sono riservati. |
| SendFeedback | \<a href="{0}" {1}>Inviare \</a> commenti e suggerimenti su questo argomento a Microsoft. |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Funzionalità: | **Dichiarazione di non responsabilità** |
| Usare: | Set di dichiarazioni di non responsabilità specifiche del caso per il contenuto tradotto automaticamente. |
| **elemento** | **Valore** |
| MT_Editable | Questo articolo è stato tradotto automaticamente. Se si dispone di una connessione Internet, selezionare "Visualizza questo argomento online" per visualizzare questa pagina in modalità modificabile con il contenuto in lingua inglese originale contemporaneamente. |
| MT_NonEditable | Questo articolo è stato tradotto automaticamente. Se si dispone di una connessione Internet, selezionare "Visualizza questo argomento online" per visualizzare questa pagina in modalità modificabile con il contenuto in lingua inglese originale contemporaneamente. |
| MT_QualityEditable | Questo articolo è stato tradotto manualmente. Se si dispone di una connessione Internet, selezionare "Visualizza questo argomento online" per visualizzare questa pagina in modalità modificabile con il contenuto in lingua inglese originale contemporaneamente. |
| MT_QualityNonEditable | Questo articolo è stato tradotto manualmente. Se si dispone di una connessione Internet, selezionare "Visualizza questo argomento online" per visualizzare questa pagina in modalità modificabile con il contenuto in lingua inglese originale contemporaneamente. |
| MT_BetaContents | Questo articolo è stato tradotto automaticamente per una versione preliminare. Se si dispone di una connessione Internet, selezionare "Visualizza questo argomento online" per visualizzare questa pagina in modalità modificabile con il contenuto in lingua inglese originale contemporaneamente. |
| MT_BetaRecycledContents | Questo articolo è stato tradotto manualmente per una versione preliminare. Se si dispone di una connessione Internet, selezionare "Visualizza questo argomento online" per visualizzare questa pagina in modalità modificabile con il contenuto originale in lingua inglese contemporaneamente. |
| Funzionalità: | **Oggetto LinkTable** |
| Usare: | Supporto per i collegamenti agli argomenti online |
| **elemento** | **Valore** |
| LinkTableTitle | Collega tabella |
| TopicEnuLinkText | Visualizzare la versione \</a> in lingua inglese di questo argomento disponibile nel computer. |
| TopicOnlineLinkText | Visualizzare questo argomento \<a href="{0}" {1}> online\</a> |
| OnlineText | Online |
| Funzionalità: | **Controllo audio video** |
| Usare: | Visualizzare elementi e testo per il contenuto video |
| **elemento** | **Valore** |
| MultiMediaNotSupported | Internet Explorer 9 o versione successiva deve essere installato per supportare il {0} contenuto. |
| Videotext | visualizzazione di video |
| AudioText | streaming di audio |
| OnlineVideoLinkText | \<p>Per visualizzare il video associato a questo argomento, fare clic {0} \<a href="{1}"> {2} \</a> qui.\</p> |
| OnlineAudioLinkText | \<p>Per ascoltare l'audio associato a questo argomento, fare clic {0} \<a href="{1}"> {2} \</a> qui.\</p> |
| Funzionalità: | **Controllo Contenuto non installato** |
| Usare: | Elementi di testo (stringhe) usati per il rendering di contentnotinstalled.htm |
| **elemento** | **Valore** |
| ContentNotInstalledTitle | Nel computer non è stato trovato alcun contenuto. |
| ContentNotInstalledDownloadContentText | \<p>Per scaricare il contenuto nel computer, \<a href="{0}" {1}> fare clic sulla scheda Gestisci \</a> .\</p> |
| ContentNotInstalledText | \<p>Nel computer non è installato alcun contenuto. Per l'installazione del contenuto della Guida locale, vedere l'amministratore.\</p> |
| Funzionalità: | **Controllo Argomento non trovato** |
| Usare: | Elementi di testo (stringhe) usati per il rendering di topicnotfound.htm |
| **elemento** | **Valore** |
| TopicNotFoundTitle | Impossibile trovare l'argomento richiesto nel computer. |
| TopicNotFoundViewOnlineText | \<p>L'argomento richiesto non è stato trovato nel computer, ma è possibile \<a href="{0}" {1}> visualizzare l'argomento \</a> online.\</p> |
| TopicNotFoundDownloadContentText | \<p>Vedere il riquadro di spostamento per i collegamenti ad argomenti simili oppure fare \<a href="{0}" {1}> clic sulla scheda Gestisci per scaricare il contenuto nel \</a> computer.\</p> |
| TopicNotFoundText | \<p>L'argomento richiesto non è stato trovato nel computer.\</p> |
| Funzionalità: | **Controllo degli argomenti danneggiati** |
| Usare: | Elementi di testo (stringhe) usati per il rendering di topiccorrupted.htm |
| **elemento** | **Valore** |
| ArgomentoCorruptedTitle | Impossibile visualizzare l'argomento richiesto. |
| TopicCorruptedViewOnlineText | \<p>Help Viewer non è in grado di visualizzare l'argomento richiesto. Potrebbe essere presente un errore nel contenuto dell'argomento o una dipendenza di sistema sottostante.\</p> |
| Funzionalità: | **Controllo Home Page** |
| Usare: | Testo che supporta la visualizzazione del contenuto del nodo di primo livello di Help Viewer. |
| **elemento** | **Valore** |
| HomePageTitle | Home page del visualizzatore della Guida |
| HomePageIntroduction | \<p>Benvenuti nel Microsoft Help Viewer, una fonte essenziale di informazioni per tutti gli utenti che utilizzano strumenti, prodotti, tecnologie e servizi Microsoft. Help Viewer consente di accedere a informazioni dettagliate e di riferimento, codice di esempio, articoli tecnici e altro ancora. Per trovare il contenuto necessario, esplorare il sommario, usare la ricerca full-text o spostarsi all'interno del contenuto usando l'indice delle parole chiave.\</p> |
| HomePageContentInstallText | \<p>\<br />Usare la \<a href="{0}" {1}> scheda Gestisci contenuto per eseguire le operazioni \</a> seguenti: Aggiungere contenuto al \<ul> \<li> computer. \</li> \<li> Verificare la disponibilità di aggiornamenti per il contenuto locale. \</li> \<li> Rimuovere il contenuto dal computer.\</li>\</ul>\</p> |
| HomePageInstalledBooks | Libri installati |
| HomePageNoBooksInstalled | Nel computer non è stato trovato alcun contenuto. |
| HomePageHelpSettings | Impostazioni del contenuto della Guida |
| HomePageHelpSettingsText | \<p>L'impostazione corrente è la Guida locale. Il Visualizzatore della Guida visualizza il contenuto installato nel computer. \<br /> Per modificare l'origine del contenuto della Guida, nella barra dei menu Visual Studio scegliere \<span style="{0}"> Guida, Imposta preferenza Guida \</span> .\<br />\</p> |
| MegaByte | MB |

**branding.js**

Il branding.js file contiene JavaScript usato dagli elementi di personalizzazione Visual Studio Help Viewer.  Di seguito è riportato un elenco degli elementi di personalizzazione e della funzione JavaScript di supporto.  Tutte le stringhe da localizzare per questo file sono definite nella sezione "Stringhe localizzabili" all'inizio di questo file.  Il file ICL è stato creato per le stringhe loc all'interno branding.js file.

|**Funzionalità di personalizzazione**|**Funzione JavaScript**|**Descrizione**|
|-|-|-|
|Var...||Definire le variabili|
|Ottenere la lingua del codice utente|setUserPreferenceLang|esegue il mapping di un indice # al linguaggio del codice|
|Impostare e ottenere i valori dei cookie|getCookie, setCookie||
|Membro ereditato|changeMembersLabel|Espandi/comprimi membro ereditato|
|When SelfBranded=False|Onload|Leggere la stringa di query per verificare se si tratta di una richiesta di stampa.  Impostare tutti i codicinippets per mettere a fuoco la scheda preferita dell'utente.  Se si tratta di una richiesta di stampa, impostare isPrinterFriendly su true. Verificare la modalità a contrasto elevato.|
|Frammento di codice|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||Tabella delle modifiche||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|Area comprimibile|addToCollapsibleControlSet|scrivere tutto l'oggetto controllo comprimibile nell'elenco.|
||CA_Click|in base allo stato dell'area comprimibile, definisce l'immagine e il testo da presentare|
|Supporto del contrasto per il logo|isBlackBackground()|Chiamato per determinare se lo sfondo è nero.  Accurato solo in modalità a contrasto elevato.|
||isHighContrast()|usare un intervallo colorato per rilevare la modalità a contrasto elevato|
||onHighContrast(black)|Chiamato quando viene rilevato un contrasto elevato|
|Funzionalità LST|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Funzionalità multimedia|caption(begin, end, text, style)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(node)||
||styleRectify(styleName, styleValue)||
||showCC(id)||
||subtitle(id)||

**FILE HTM**

Il pacchetto di personalizzazione contiene un set di file HTM che supportano scenari per la comunicazione delle informazioni chiave agli utenti del contenuto della Guida, ad esempio una home page che contiene una sezione che descrive i set di contenuto installati e pagine che informano l'utente quando non è possibile trovare argomenti nel set locale di argomenti. Questi file HTM possono essere modificati per prodotto.  I fornitori di ISO Shell possono usare il pacchetto di personalizzazione predefinito e modificare il comportamento e il contenuto di queste pagine in base alle proprie necessità.  Questi file fanno riferimento al rispettivo pacchetto di personalizzazione per consentire ai tag di personalizzazione di ottenere il contenuto corrispondente branding.xml file.

|**File**|**Uso**|**Origine contenuto visualizzato**|
|-|-|-|
|homepage.htm|Si tratta di una pagina che visualizza il contenuto attualmente installato e qualsiasi altro messaggio appropriato per presentare all'utente il contenuto.  Questo file ha l'attributo dei metadati aggiuntivo "Microsoft.Help.Id" content="-1" che posiziona questo contenuto all'inizio del sommario del contenuto locale.||
||<META_HOME_PAGE_TITLE_ADD />|Branding.xml, tag \<HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|Branding.xml, tag \<HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.xml, tag \<HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|La sezione Branding.xml tag \<HomePageInstalledBooks> , i dati generati dall'applicazione, quando non sono installati  \<HomePageNoBooksInstalled> libri.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|Sezione intestazione Branding.xml tag \<HomePageHelpSettings> , testo della sezione \<HomePageHelpSettingsText> .|
|topiccorrupted.htm|Quando un argomento esiste nel set locale, ma per qualche motivo non può essere visualizzato (contenuto danneggiato).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding.xml, tag \<TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding.xml, tag \<TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Quando un argomento non viene trovato nel set di contenuti locale, né è disponibile online||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.xml, tag \<TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD />|Branding.xml, tag \<TopicNotFoundViewOnlineText> + \<TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD />|Branding.xml, tag \<TopicNotFoundText>|
|contentnotinstalled.htm|Quando non è installato alcun contenuto locale per il prodotto.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding.xml, tag \<ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding.xml, tag \<ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|Branding.xml, tag \<ContentNotInstalledText>|

**File CSS**

Il Visual Studio di personalizzazione di Help Viewer contiene due file CSS per supportare la coerenza Visual Studio presentazione del contenuto della Guida:

- Branding.css: contiene elementi CSS per il rendering in cui SelfBranded=false

- Printer.css: contiene elementi CSS per il rendering in cui SelfBranded=false

I file Branding.css includono le definizioni per la presentazione di un argomento Visual Studio (si noti che il file branding.css contenuto nel file con estensione mshc di Branding_ dal servizio pacchetti può \<locale> cambiare).

**File grafici**

Visual Studio contenuto visualizza un logo Visual Studio e altri elementi grafici.  Di seguito è riportato l'elenco completo dei file grafici Visual Studio pacchetto di personalizzazione di Help Viewer.

|**File**|**Uso**|**esempi**|
|-|-|-|
|clear.gif|Usato per eseguire il rendering dell'area comprimibile||
|footer_slice.gif|Presentazione del piè di pagina||
|info_icon.gif|Usato per la visualizzazione di informazioni|Dichiarazione di non responsabilità|
|online_icon.gif|Questa icona deve essere associata ai collegamenti online||
|tabLeftBD.gif|Usato per eseguire il rendering del contenitore del frammento di codice||
|tabRightBD.gif|Usato per eseguire il rendering del contenitore del frammento di codice||
|vs_logo_bk.gif|Usato per i riferimenti al logo a contrasto normale, come definito nel tag Branding.xml \<LogoFileName> .  Per Visual Studio prodotti, il nome del logo è vs_logo_bk.gif.||
|vs_logo_wh.gif|Usato per i riferimenti al logo a contrasto elevato, come definito Branding.xml tag \<LogoFileNameHC> .  Per Visual Studio prodotti, il nome del logo è vs_logo_wh.gif.||
|ccOff.png|Immagine di sottotitoli||
|ccOn.png|Immagine di sottotitoli||
|ImageSprite.png|Usato per eseguire il rendering dell'area comprimibile|immagine espansa o compressa|

## <a name="deploy-a-set-of-topics"></a>Distribuire un set di argomenti

Si tratta di un'esercitazione semplice e rapida per la creazione di un set di distribuzione del contenuto di Help Viewer costituito da un file MSHA e dal set di file CAB o MSHC contenenti gli argomenti. MSHA è un file XML che descrive un set di file cab o MSHC. Help Viewer può leggere L'MSHA per ottenere un elenco di contenuto (il .CAB o . file MSHC) disponibili per l'installazione locale.

Si tratta solo di una nozioni di base che descrive l'XML Schema di base per Help Viewer MSHA.  Di seguito è riportata una breve panoramica e un esempio di implementazione di HelpContentSetup.msha.

Il nome della MSHA, ai fini di questa guida di base, è HelpContentSetup.msha (il nome del file può essere qualsiasi elemento, con estensione . MSHA). HelpContentSetup.msha (esempio riportato di seguito) deve contenere un elenco dei cab o dei MSHC disponibili.  Il tipo di file deve essere coerente all'interno di MSHA (non supporta una combinazione di tipi di file MSHA e CAB). Per ogni CAB o MSHC deve essere presente \<div class="package"> un... \</div> (vedere l'esempio seguente).

Nota: nell'esempio di implementazione seguente è stato incluso il pacchetto di personalizzazione. Questo è fondamentale da includere per ottenere il contenuto necessario per Visual Studio elementi di rendering del contenuto e i comportamenti del contenuto.

File HelpContentSetup.msha di esempio: sostituire "content set name 1" e "content set name 2" e così via con i nomi dei file.

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

1. Creare una cartella locale, ad esempio "C:\SampleContent"

2. Per questo esempio verranno utilizzati file MSHC per contenere gli argomenti.  Un file MSHC è un file ZIP con l'estensione del file modificata da .zip a . MSHC.

3. Creare il file HelpContentSetup.msha seguente come file di testo (il Blocco note è stato usato per creare il file) e salvarlo nella cartella sopra riportata (vedere il passaggio 1).

La classe "Branding" esiste ed è univoca. Il file mshc di personalizzazione è incluso in questa guida di base in modo che il contenuto installato abbia informazioni di personalizzazione e i comportamenti del contenuto contenuti nei MSHC avranno gli elementi di supporto appropriati contenuti nel pacchetto di personalizzazione. In caso contrario, si verificano errori quando il sistema cerca elementi di supporto che non fanno parte del contenuto decompresso (installato).

Per ottenere il pacchetto di personalizzazione Visual Studio, copiare il file Branding_en-US.mshc in C:\Programmi (x86)\Microsoft Help Viewer\v2.3\ nella cartella di lavoro.

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

**Summary**

L'uso e l'estensione dei passaggi precedenti consentiranno ai VSP di distribuire i relativi set di contenuti per Visual Studio Help Viewer.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Aggiungere la Guida alla shell Visual Studio (integrata e isolata)

**Introduzione**

Questa procedura dettagliata illustra come incorporare il contenuto della Guida in un Visual Studio Shell e quindi distribuirlo.

**Requisiti**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 Isolated Shell Redist](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Panoramica**

La [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] shell è una versione dell'IDE su cui è possibile [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] basare un'applicazione. Tali applicazioni contengono Isolated Shell insieme alle estensioni create dall'utente. Usare i modelli di progetto della shell isolata, inclusi [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] nell'SDK, per compilare le estensioni.

I passaggi di base per la creazione di un'applicazione basata su Isolated Shell e della relativa Guida:

1. Ottenere [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] isO Shell Redistributable (download Microsoft).

2. In Visual Studio creare un'estensione della Guida basata su Isolated Shell, ad esempio l'estensione della Guida di Contoso descritta più avanti in questa procedura dettagliata.

3. Eseguire il wrapping dell'estensione e della shell ISO ridistribuibile in un file MSI di distribuzione (configurazione dell'applicazione). Questa procedura dettagliata non include un passaggio di configurazione.

Creare un archivio Visual Studio contenuto. Per lo scenario della shell integrata, modificare Visual Studio12 con il nome del catalogo prodotti come indicato di seguito:

- Creare la cartella C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.

- Creare un file CatalogType.xml e aggiungerlo alla cartella . Il file deve contenere le righe di codice seguenti:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Definire l'archivio del contenuto nel Registro di sistema. Per la shell integrata, sostituire VisualStudio15 con il nome del catalogo prodotti:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

   Chiave: Valore stringa LocationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US

   Chiave: Valore stringa CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Documentation

**Creare il progetto**

Per creare un'estensione della shell isolata:

1. In Visual Studio, in **File** scegliere Nuovo progetto  **,** in Altri tipi di progetto scegliere **Estendibilità** e quindi scegliere Visual Studio Shell **isolata.** Assegnare al progetto il nome ) per creare un progetto di estendibilità basato `ContosoHelpShell` sul Visual Studio Isolated Shell.

2. Nel Esplora soluzioni ContosoHelpShellUI aprire ApplicationCommands.vsct nella cartella File di risorse. Assicurarsi che questa riga sia impostata come commento (cercare "No_Help"): `<!-- <define name="No_HelpMenuCommands"/> -->`

3. Premere F5 per compilare ed eseguire **Debug**. Nell'istanza sperimentale dell'IDE della shell isolata scegliere il menu **?** . Assicurarsi che vengano visualizzati i comandi **Visualizza** guida , **Aggiungi e** Rimuovi contenuto della Guida e Imposta **preferenza** Guida .

4. Nella Esplora soluzioni Shell del progetto ContosHelpShell aprire ContosoHelpShell.pkgdef nella cartella Personalizzazione shell. Per definire il catalogo della Guida di Contoso, aggiungere le righe seguenti:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. Nella Esplora soluzioni Shell del progetto ContosHelpShell aprire ContosoHelpShell.Application.pkgdef nella cartella Personalizzazione shell. Per abilitare la Guida F1, aggiungere le righe seguenti:

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

6. Nel Esplora soluzioni di scelta rapida della soluzione ContosoHelpShell scegliere la **voce di** menu Proprietà. In **Proprietà di configurazione** selezionare **Gestione configurazione**. Nella colonna **Configurazione** modificare ogni valore "Debug" in "Release".

7. Compilare la soluzione. Verrà creato un set di file in una cartella release, che verrà usata nella sezione successiva.

Per eseguire il test come se fosse stato distribuito:

1. Nel computer in cui si distribuisce Contoso installare la shell ISO scaricata (dalla precedente).

2. Creare una cartella in \\ \Programmi (x86) \\ e denomerla `Contoso` .

3. Copiare il contenuto dalla cartella della versione ContosoHelpShell alla \\ cartella \Programmi (x86)\Contoso\.

4. Avviare l'editor del Registro di sistema  **scegliendo** Esegui dal menu **Start** e immettendo `Regedit` . Nell'editor del Registro di sistema **scegliere File** e quindi **Importa.** Passare alla cartella del progetto ContosoHelpShell. Nella sottocartella ContosoHelpShell scegliere ContosoHelpShell.reg.

5. Creare un archivio del contenuto:

    Per la shell ISO, creare un archivio del contenuto Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

    Per [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell integrata, creare la cartella C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15

6. Creare CatalogType.xml e aggiungere all'archivio del contenuto (passaggio precedente) contenente:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Aggiungere le chiavi del Registro di sistema seguenti:

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: Valore stringa LocationPath:

    Per la shell ISO:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell integrata:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Chiave: Valore stringa CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Documentation. Per ISO Shell, questo è il nome del catalogo.

8. Copiare il contenuto (cab o MSHC e MSHA) in una cartella locale.

9. Esempio di riga di comando della shell integrata per testare l'archivio del contenuto. Per ISO Shell, modificare i valori catalog e launchingApp in modo che corrispondano al prodotto.

     "C:\Programmi (x86)\Microsoft Help Viewer\v2.3\HlpViewer.exe" /catalogName VisualStudio15 /helpQuery method="page&id=ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. Avviare l'applicazione Contoso (dalla radice dell'app Contoso). Nella shell ISO scegliere la voce **di** menu Guida e impostare **l'opzione Imposta preferenza Guida** su Usa Guida **locale**.

11. Nella shell scegliere la voce di menu **Guida** e quindi **Visualizza Guida.** Verrà avviato il visualizzatore della Guida locale. Scegliere la **scheda Gestisci** contenuto. In **Origine installazione** scegliere il pulsante di **opzione** Disco. Scegliere il **pulsante ...** e passare alla cartella locale contenente il contenuto di Contoso (copiato nella cartella locale nel passaggio precedente). Scegliere HelpContentSetup.msha. Contoso dovrebbe ora essere visualizzato come libro nelle selezioni dei libri. Scegliere **Aggiungi** e quindi scegliere il **pulsante Aggiorna** nell'angolo in basso a destra.

12. Nell'IDE di Contoso premere F1 per testare la funzionalità F1.

## <a name="additional-resources"></a>Risorse aggiuntive

Per l'API di runtime, vedere [API della Guida di Windows.](/previous-versions/windows/desktop/helpapi/helpapi-portal)

Per altre informazioni su come sfruttare l'API Della Guida, vedere [Esempi di codice di Help Viewer.](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples)

È possibile inviare suggerimenti sulle funzionalità [Developer Community](https://aka.ms/feedback/suggest?space=8).
