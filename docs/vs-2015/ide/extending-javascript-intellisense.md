---
title: Estensione di IntelliSense in JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e995d9cfd37c625c03df0b607a9dd5184bec5d08
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441470"
---
# <a name="extending-javascript-intellisense"></a>Estensione di IntelliSense in JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La funzionalità di estensibilità JavaScript IntelliSense consente di personalizzare i risultati di IntelliSense nell'editor JavaScript per le librerie di terze parti. Ciò può migliorare l'esperienza degli sviluppatori che utilizzano queste librerie.  
  
 Il servizio JavaScript language service fornisce le funzionalità di IntelliSense per le librerie JavaScript di terze parti che vengono aggiunti a un progetto. Per la maggior parte delle librerie, completamento delle istruzioni viene fornito automaticamente dal servizio di linguaggio. La figura seguente mostra un esempio di completamento delle istruzioni:  
  
 ![Esempio di completamento delle istruzioni](../ide/media/js-intellisense-completion.png "js_intellisense_completion")  
  
 Se la libreria include le descrizioni delle variabili, funzioni e gli oggetti nel tag di commento JavaScript standard (/ /), usufruiscono automaticamente, per impostazione predefinita, dalle funzionalità di estendibilità di IntelliSense, che forniscono informazioni descrittive in una finestra popup che viene visualizzato a destra di elementi in un elenco di completamento, o quando si digita la parentesi di apertura in una chiamata di funzione. I commenti nella casella popup contengono la descrizione del membro. Nell'esempio seguente mostra la finestra popup per un elenco di completamento.  
  
 ![Esempio di un pop di informazioni rapide&#45;finestra di dialogo](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")  
  
 Per migliorare ulteriormente l'esperienza di sviluppo, si potrebbe voler fornire informazioni sul tipo per gli sviluppatori nella finestra di popup. È possibile fornire le informazioni sul tipo con JavaScript [commenti in formato documentazione XML](../ide/xml-documentation-comments-javascript.md) invece di tag di commento standard. Aggiungere commenti in formato documentazione XML tramite i tag di commenti a barra tripla (/ / /) e un set definito di elementi XML.  
  
 In alternativa, è possibile fornire le informazioni sul tipo usando l'estensibilità JavaScript IntelliSense. Questa funzionalità consente di personalizzare i risultati di IntelliSense per la creazione di estensioni di JavaScript e aggiungendoli al contesto di script. Per l'estensione, ovvero un file JavaScript, si sottoscrive gli eventi esposti dal `intellisense` oggetto del servizio di linguaggio. Estensibilità JavaScript IntelliSense è la soluzione preferita per le raccolte se un modello di comportamento nella libreria impedisce che il servizio JavaScript language service che fornisce il livello desiderato di supporto di IntelliSense e un'alternativa alla sintassi XML dichiarativa È necessario anche per i commenti della documentazione. Personalizzando i risultati di IntelliSense, è possibile creare un'eccellente esperienza di IntelliSense, indipendentemente dalle eventuali modelli di comportamento che potrebbe limitare le funzionalità predefinite del servizio di linguaggio. Per altre informazioni, vedere [Completamento delle istruzioni per gli identificativi](../ide/statement-completion-for-identifiers.md).  
  
## <a name="adding-an-extension-to-the-script-context"></a>Aggiunta di un'estensione per il contesto di Script  
 Per un'estensione di IntelliSense a essere eseguito, deve essere aggiunto al contesto script corrente. L'estensione può essere aggiunti automaticamente al contesto di script tramite il meccanismo di individuazione automatica oppure è possibile aggiungere manualmente l'estensione per il contesto di script usando i gruppi di riferimento o la direttiva di riferimento.  
  
 Il meccanismo di individuazione automatica consente al servizio di linguaggio trovare automaticamente le estensioni che seguono la convenzione di denominazione file *NomeLibreria*. intellisense.js e che si trovano nella stessa directory della libreria di che viene applicata l'estensione. Ad esempio, un'estensione valida per la libreria jQuery sarebbe jQuery.intellisense.js. Le estensioni di jQuery più restrittive, è possibile usare nomi di file, ad esempio jQuery-1.7.1.intellisense.js (un'estensione specifica di versione) o jQuery.ui.intellisense.js (un'estensione per una libreria jQuery con ambito). La versione più restrittiva dell'estensione viene usata se non viene trovata più di un'estensione per una determinata libreria.  
  
 Se si desidera usare l'estensione per tutti i file di progetto di JavaScript, è invece possibile scegliere aggiungere l'estensione a un gruppo di riferimento. Esistono diversi tipi di gruppi di riferimenti, quelle che includono riferimenti impliciti e quelle che includono riferimenti ruolo di lavoro dedicato. Per aggiungere un'estensione, in genere è necessario aggiungere il file come un gruppo di riferimento implicito, ovvero **implicite (Windows)**, **implicito (Web)**. Riferimenti impliciti sono inclusi nell'ambito per ogni file con estensione js aperto nell'Editor del codice. Quando si usa questo metodo, è necessario aggiungere il file che l'estensione è integrando sia all'estensione.  
  
 Usare la **IntelliSense** pagina della **opzioni** finestra di dialogo per aggiungere un'estensione come un gruppo di riferimento. È possibile accedere il **IntelliSense** pagina scegliendo **Tools**, **opzioni** sulla barra dei menu e scegliendo **Editor di testo**, **JavaScript**, **IntelliSense**, **riferimenti**. Per altre informazioni sui gruppi di riferimenti, vedere [IntelliSense per JavaScript](../ide/javascript-intellisense.md) e [opzioni, Editor di testo, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).  
  
 Se si desidera usare l'estensione di un set specifico di file, usare una direttiva di riferimento. Quando si usa questo metodo, è necessario fare riferimento sia all'estensione di file è che completano l'estensione. Per informazioni sull'utilizzo della direttiva di riferimento, vedere [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
## <a name="handling-intellisense-events"></a>Gestione degli eventi di IntelliSense  
 La funzionalità di estendibilità consente di personalizzare i risultati di IntelliSense, sottoscrivere gli eventi, ad esempio la `statementcompletion` eventi del servizio di linguaggio `intellisense` oggetto. L'esempio seguente illustra una semplice estensione utilizzato dal servizio di linguaggio per nascondere i membri che iniziano con un carattere di sottolineatura dal completamento delle istruzioni. Questo codice è contenuto in underscorefilter.js ed è nel \\ \\ *il percorso di installazione di Visual Studio*\JavaScript\References cartella.  
  
```javascript  
intellisense.addEventListener('statementcompletion', function (event) {  
    if (event.targetName === "this") return;  
  
    var filterRegex;  
  
    if (event.target === undefined || event.target === window)  
        filterRegex = /^_.*\d{2,}/;  
    else  
        filterRegex = /^_.*/;  
  
    event.items = event.items.filter(function (item) {  
        return !filterRegex.test(item.name);  
    });  
});  
```  
  
 Nel codice precedente, l'estensione verifica il [proprietà targetName](#TargetName) e [destinata alla proprietà](#Target) le proprietà del `statementcompletion` oggetto evento escludere gli oggetti, ad esempio `this` e`window`e per garantire che possa essere identificato un elenco di completamento istruzione valida. Se può essere identificato un elenco di completamento, l'estensione viene aggiornato il completamento delle istruzioni [proprietà degli elementi](#Items) raccolta escludendo i membri che iniziano con un carattere di sottolineatura.  
  
 Per altri esempi, consultare il \\ \\ *il percorso di installazione di Visual Studio*\JavaScript\References cartella. Il file showPlainComments.js in questa cartella vengono forniti esempi dell'uso di altri eventi per fornire il supporto IntelliSense predefinito per i tag di commento JavaScript standard (/ /). Ad esempio underscorefilter.js, showPlainComments.js è già disponibile come estensione di lavoro ed è possibile visualizzare le informazioni risultanti di IntelliSense quando si usano i tag di commento nel codice per le variabili, funzioni e oggetti. Per altri esempi, vedere [esempi di codice](#CodeExamples).  
  
> [!WARNING]
> Se si modificano i file di estensione forniti con Visual Studio, è possibile disabilitare IntelliSense per JavaScript o funzionalità supportata dall'estensione.  
  
 Nel codice dell'estensione, è possibile creare gestori per i seguenti tipi di evento utilizzando `addEventListener`:  
  
- `statementcompletion`, che aggiunge un gestore per un evento di completamento dell'istruzione. Completamento delle istruzioni fornisce un elenco di membri per un determinato tipo che viene visualizzato dopo aver digitato un carattere speciale, ad esempio un punto (.) o un elenco di identificatori che viene visualizzato durante la digitazione o quando si preme CTRL + J. Il gestore riceve un oggetto evento di tipo `CompletionEvent`, che supporta i membri seguenti: [proprietà degli elementi](#Items), [proprietà di destinazione](#Target), [targetName proprietà](#TargetName), e [ambito proprietà](#Scope).  
  
- `signaturehelp`, che aggiunge un gestore per le informazioni sul parametro di IntelliSense. Informazioni sul parametro fornisce informazioni su numero, nomi e tipi di parametri richiesti da una funzione. Il gestore riceve un oggetto evento di tipo `SignatureHelpEvent`, che supporta i membri seguenti: [proprietà di destinazione](#Target), [parentObject proprietà](#ParentObject), [functionComments proprietà](#FunctionComments), [functionHelp proprietà](#FunctionHelp).  
  
- `statementcompletionhint`, che aggiunge un gestore per le informazioni rapide di IntelliSense. La casella popup informazioni rapide visualizza la dichiarazione completa per gli identificatori nel codice. Il gestore riceve un oggetto evento di tipo `CompletionHintEvent`, che supporta i membri seguenti: [completionItem proprietà](#CompletionItem), e [symbolHelp proprietà](#SymbolHelp).  
  
  Per esempi che illustrano le caratteristiche IntelliSense come il completamento delle istruzioni, informazioni sul parametro e informazioni rapide, vedere [uso di IntelliSense](../ide/using-intellisense.md).  
  
> [!NOTE]
> In JavaScript, informazioni rapide si intende la finestra popup che viene visualizzato a destra di un elenco di completamento. È possibile richiamare manualmente le informazioni rapide.  
  
## <a name="intellisenseObject"></a> Oggetto IntelliSense  
 Nella tabella seguente mostra le funzioni che sono disponibili per il `intellisense` oggetto. Il `intellisense` oggetto è disponibile solo in fase di progettazione.  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|`addEventListener(type, handler);`|Aggiunge un gestore eventi per un evento di IntelliSense.<br /><br /> `type` è un valore stringa. I valori validi includono `statementcompletion`, `signaturehelp` e `statementcompletionhint`.<br /><br /> `handler` è una funzione del gestore eventi che riceve un oggetto evento di uno dei tipi seguenti:<br /><br /> -   `CompletionEvent`, usato per il `statementcompletion` evento.<br />-   `SignatureHelpEvent`, usato per il `signaturehelp` evento.<br />-   `CompletionHintEvent`, usato per il `statementcompletionhint` evento.<br /><br /> Per esempi che usano questa funzione, vedere [esempi di codice](#CodeExamples).|  
|`annotate(obj, doc);`|Specifica la documentazione per un oggetto copiando i commenti della documentazione da un oggetto in un altro oggetto.<br /><br /> `obj` Specifica l'oggetto da cui copiare la documentazione.<br /><br /> `doc` Specifica l'oggetto da cui copiare la documentazione.<br /><br /> Per un esempio che illustra come usare questa funzione, vedere [aggiunta di annotazioni IntelliSense](#Annotations).|  
|`getFunctionComments(func);`|Restituisce i commenti per una funzione specificata.<br /><br /> `func` Specifica la funzione per il quale vengono restituiti i commenti.<br /><br /> È possibile impostare il `func` parametro usando `completionItem.value`.<br /><br /> L'oggetto restituito `functionComments` oggetto include i membri seguenti: `above`, `inside`, e `paramComment`. Per altre informazioni, vedere la [functionComments proprietà](#FunctionComments) proprietà.<br /><br /> `getFunctionComments` può essere chiamato solo da all'interno di uno dei gestori di eventi che sono registrati per `addEventListener`.<br /><br /> Per un esempio che illustra come usare questa funzione, vedere \\ \\ *il percorso di installazione di Visual Studio*\JavaScript\References\showPlainComments.js.|  
|`logMessage(msg);`|Invia i messaggi diagnostici nella finestra di Output.<br /><br /> `msg` è una stringa che contiene il messaggio.<br /><br /> Per un esempio che illustra come usare questa funzione, vedere [invio di messaggi nella finestra di Output](#Logging).|  
|`nullWithCompletionsOf(value);`|Restituisce un valore null speciale per i quali l'elenco di completamento è determinato dall'oggetto passato il `value` parametro.<br /><br /> `value` Determina l'elenco di completamento per il valore restituito. `value` può essere qualsiasi tipo.<br /><br /> Il valore restituito null viene considerato null in fase di progettazione, ma l'elenco di completamento per il valore restituito è quello utilizzato per l'elenco di completamento per il `value` parametro.<br /><br /> È possibile utilizzare questa funzione consiste nel fornire IntelliSense per un valore restituito quando il tipo restituito è prevedibile in fase di esecuzione, ma il valore restituito è `null` in fase di progettazione.|  
|`redirectDefinition(func, definition);`|Indica a IntelliSense da usare la funzione di definizione specificata anziché la funzione func originale quando la Guida ai parametri oppure **Vai a definizione** viene richiesto.<br /><br /> `func` Specifica la funzione di destinazione.<br /><br /> `definition` Specifica la funzione da utilizzare invece la funzione di destinazione per le informazioni sui parametri e **Vai a definizione**.|  
|`setCallContext(func, thisArg);`|Imposta il contesto di chiamata, o ambito, per la funzione specificata.<br /><br /> `func` Specifica la funzione per cui impostare l'ambito.<br /><br /> `thisArg` è un oggetto letterale a cui il `this` parola chiave farvi riferimento, che consente di specificare il nuovo ambito per il membro. È possibile includere gli argomenti da passare in questo parametro, ad esempio, `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` fornisce un comportamento simile a `Function.prototype.bind`, ad eccezione del fatto che usato solo per il supporto di IntelliSense in fase di progettazione. È possibile usare `setCallContext` per impostare l'ambito della funzione se è necessario simulare una chiamata a codice non raggiungibile in caso contrario, in modo che quando si chiama la funzione, la chiamata di funzione includerà l'ambito corretto e gli argomenti.|  
|`undefinedWithCompletionsOf(value);`|Restituisce un valore speciale non definito per il quale l'elenco di completamento è determinato dall'oggetto passato il `value` parametro.<br /><br /> `value` Determina l'elenco di completamento per il valore restituito. `value` può essere qualsiasi tipo.<br /><br /> Restituisce il undefined valore viene trattato come definito in fase di progettazione, ma il completamento elenco per il valore restituito è quello utilizzato per l'elenco di completamento per il `value` parametro.<br /><br /> È possibile utilizzare questa funzione consiste nel fornire IntelliSense per un valore restituito quando il tipo restituito è prevedibile in fase di esecuzione, ma il valore restituito è definito in fase di progettazione.|  
|`version()`|Restituisce la versione di Visual Studio.|  
  
## <a name="event-members"></a>Membri di evento  
 Le sezioni seguenti descrivono i membri vengono esposti nell'oggetto di eventi per gli eventi seguenti: `statementcompletion`, `signaturehelp`, e `statementcompletionhint`.  
  
### <a name="CompletionItem"></a> completionItem proprietà  
 Restituisce l'identificatore, noto come elemento di completamento, per cui è richiesto una casella popup informazioni rapide. Questa proprietà è disponibile per il `statementcompletionhint` oggetto dell'evento e per il [proprietà degli elementi](#Items) proprietà del `statementcompletion` oggetto evento.  
  
 Valore restituito: `completionItem` oggetto  
  
 Di seguito sono i membri del `completionItem` oggetto:  
  
- `name`. Lettura/scrittura se utilizzato nel `items` raccolta; in caso contrario, sola lettura. Restituisce una stringa che identifica l'elemento di completamento.  
  
- `kind`. Lettura/scrittura se utilizzato nel `items` raccolta; in caso contrario, sola lettura. Restituisce una stringa che rappresenta il tipo di elemento di completamento. I valori possibili sono metodo, campo, proprietà, parametro, variabile e sono riservati.  
  
- `glyph`. Lettura/scrittura se utilizzato nel `items` raccolta; in caso contrario, sola lettura. Restituisce una stringa che rappresenta un'icona che viene visualizzata nell'elenco di completamento. I valori possibili per `glyph` usare il formato seguente: Visual Studio:*glyphType*, dove *glyphType* corrisponde ai membri indipendenti dal linguaggio di <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> enumerazione. Ad esempio, `vs:GlyphGroupMethod` è uno dei possibili valori per `glyph`. Quando `glyph` non è impostata, il `kind` proprietà determina l'icona predefinita.  
  
- `parentObject`. Sola lettura. Restituisce l'oggetto padre.  
  
- `value`. Sola lettura. Restituisce un oggetto che rappresenta il valore dell'elemento di completamento.  
  
- `comments`. Sola lettura. Restituisce una stringa che contiene i commenti che sono di sopra il campo o variabile.  
  
- `scope`. Sola lettura. Restituisce l'ambito dell'elemento di completamento. I valori possibili sono parametro globale, locale e membro.  
  
### <a name="Items"></a> Proprietà degli elementi  
 Ottiene o imposta la matrice di istruzione di elementi di completamento. Ogni elemento nella matrice è un [completionItem proprietà](#CompletionItem) oggetto. Il `items` proprietà è disponibile per il `statementcompletion` oggetto evento.  
  
 Valore restituito: array  
  
### <a name="FunctionComments"></a> functionComments proprietà  
 Restituisce i commenti per la funzione. Questa proprietà è disponibile per il `signaturehelp` oggetto evento.  
  
 Valore restituito: `comments` oggetto  
  
 Di seguito sono i membri del `comments` oggetto:  
  
- `above`. Restituisce i commenti sopra la funzione.  
  
- `inside`. Restituisce i commenti all'interno della funzione, in genere nel formato VSDoc.  
  
- `paramComments`. Restituisce una matrice che rappresenta i commenti per ogni parametro nella funzione. I membri della matrice includono:  
  
    - `name`. Restituisce una stringa che rappresenta il nome del parametro.  
  
    - `comment`. Restituisce una stringa che contiene il parametro di commento.  
  
### <a name="FunctionHelp"></a> functionHelp proprietà  
 Restituisce la Guida per la funzione. Questa proprietà è disponibile per il `signaturehelp` oggetto evento.  
  
 Valore restituito: `functionHelp` oggetto  
  
 Di seguito sono i membri del `functionHelp` oggetto:  
  
- `functionName`. Lettura/scrittura. Restituisce una stringa che contiene il nome della funzione.  
  
- `signatures`. Lettura/scrittura. Ottiene o imposta la matrice di firme di funzione. Ogni elemento nella matrice è un `signature` oggetto. Alcuni `signature` proprietà, ad esempio `locid`, corrispondono ai comuni [commenti in formato documentazione XML](../ide/xml-documentation-comments-javascript.md) attributi.  
  
     I membri del `signature` oggetto includono:  
  
    - `description`. Lettura/scrittura. Restituisce una stringa che descrive la funzione.  
  
    - `locid`. Lettura/scrittura. Restituisce un identificatore di stringa che contiene informazioni di localizzazione sulla funzione.  
  
    - `helpKeyword`. Lettura/scrittura. Restituisce una stringa che contiene la parola chiave della Guida.  
  
    - `externalFile`. Lettura/scrittura. Restituisce una stringa che rappresenta il file che contiene l'ID del membro.  
  
    - `externalid`. Lettura/scrittura. Restituisce una stringa che rappresenta l'ID del membro della funzione.  
  
    - `params`. Lettura/scrittura. Ottiene o imposta la matrice di parametri per la funzione. Ogni elemento nella matrice di parametri è un `parameter` oggetto con proprietà che corrispondono a questi attributi per il [ \<param >](../ide/param-javascript.md) elemento:  
  
        - `name`. Lettura/scrittura. Restituisce una stringa che rappresenta il nome del parametro.  
  
        - `type`. Lettura/scrittura. Restituisce una stringa che rappresenta il tipo di parametro.  
  
        - `elementType`. Lettura/scrittura. Se il tipo è `Array`, restituisce una stringa che rappresenta il tipo degli elementi nella matrice.  
  
        - `description`. Lettura/scrittura. Restituisce una stringa che descrive il parametro.  
  
        - `locid`. Lettura/scrittura. Restituisce un identificatore di stringa che contiene informazioni di localizzazione sulla funzione.  
  
        - `optional`. Lettura/scrittura. Restituisce una stringa che indica se il parametro è facoltativo. `true` indica che il parametro è facoltativo. `false` indica che non lo è.  
  
    - `returnValue`. Lettura/scrittura. Ottiene o imposta un oggetto di valore restituito con proprietà che corrispondono a questi attributi per il [ \<restituisce >](../ide/returns-javascript.md) elemento:  
  
        - `type`. Lettura/scrittura. Restituisce una stringa che rappresenta il tipo restituito.  
  
        - `elementType`. Lettura/scrittura. Se il tipo è `Array`, restituisce una stringa che rappresenta il tipo degli elementi nella matrice.  
  
        - `description`. Lettura/scrittura. Restituisce una stringa che descrive il valore restituito.  
  
        - `locid`. Lettura/scrittura. Restituisce un identificatore di stringa che contiene informazioni di localizzazione sulla funzione.  
  
        - `helpKeyword`. Lettura/scrittura. Restituisce una stringa che contiene la parola chiave della Guida.  
  
        - `externalFile`. Lettura/scrittura. Restituisce una stringa che rappresenta il file che contiene l'ID del membro.  
  
        - `externalid`. Lettura/scrittura. Restituisce una stringa che rappresenta l'ID del membro della funzione.  
  
### <a name="ParentObject"></a> parentObject proprietà  
 Restituisce l'oggetto padre di una funzione membro. Ad esempio, per `document.getElementByID`, `parentObject` restituisce il `document` oggetto. Questa proprietà è disponibile per il `signaturehelp` oggetto evento.  
  
 Valore restituito: oggetto  
  
### <a name="Target"></a> Proprietà target  
 Restituisce un oggetto che rappresenta l'elemento a sinistra del carattere trigger, ovvero un punto (.). Per le funzioni, `target` restituisce la funzione di cui vengono richieste informazioni sul parametro. Questa proprietà è disponibile per il `statementcompletion` e `signaturehelp` oggetti evento.  
  
 Valore restituito: oggetto  
  
### <a name="TargetName"></a> Proprietà targetName  
 Restituisce una stringa che rappresenta la destinazione. Ad esempio, per "this.", `targetName` restituisce "this". Per "B" (quando il cursore si trova dopo "B"), `targetName` restituisce "B". Questa proprietà è disponibile per il `statementcompletion` oggetto evento.  
  
 Valore restituito: string  
  
### <a name="SymbolHelp"></a> symbolHelp proprietà  
 Restituisce l'elemento di completamento per il quale viene richiesta una finestra popup di informazioni rapide. Questa proprietà è disponibile per il `statementcompletionhint` oggetto evento.  
  
 Valore restituito: `symbolHelp` oggetto.  
  
 Alcune proprietà del `symbolHelp` dell'oggetto, ad esempio `locid`, corrispondono ai comuni [commenti in formato documentazione XML](../ide/xml-documentation-comments-javascript.md) attributi.  
  
 Di seguito sono i membri del `symbolHelp` oggetto:  
  
- `name`. Lettura/scrittura. Restituisce una stringa che contiene il nome dell'identificatore.  
  
- `symbolType`. Lettura/scrittura. Restituisce una stringa che rappresenta il tipo di simbolo. I valori possibili includono Unknown, valore booleano, numero, stringa, oggetto, funzione, matrice, data e Regex.  
  
- `symbolDisplayType`. Lettura/scrittura. Restituisce una stringa che contiene il nome del tipo da visualizzare. Se `symbolDisplayType` non è impostato, `symbolType` viene usato.  
  
- `elementType`. Lettura/scrittura. Se il `symbolType` è `Array`, restituisce una stringa che rappresenta il tipo degli elementi nella matrice.  
  
- `scope`. Lettura/scrittura. Restituisce una stringa che rappresenta l'ambito del simbolo. I valori possibili includono parametro globale, locale e membro.  
  
- `description`. Lettura/scrittura. Restituisce una stringa che contiene una descrizione del simbolo.  
  
- `locid`. Lettura/scrittura. Restituisce un identificatore di stringa che contiene informazioni di localizzazione sul simbolo.  
  
- `helpKeyword`. Lettura/scrittura. Restituisce una stringa che contiene la parola chiave della Guida.  
  
- `externalFile`. Lettura/scrittura. Restituisce una stringa che rappresenta il file che contiene l'ID del membro.  
  
- `externalid`. Lettura/scrittura. Restituisce una stringa che rappresenta l'ID del membro del simbolo.  
  
- `functionHelp`. Lettura/scrittura. Restituisce un [functionHelp proprietà](#FunctionHelp), che potrebbe contenere informazioni quando il `symbolType` funzione.  
  
### <a name="Scope"></a> Proprietà di ambito  
 Restituisce l'ambito di completamento dell'evento. I valori possibili per il completamento di ambito sono globale e membri. Questa proprietà è disponibile per il `statementcompletion` oggetto evento.  
  
 Valore restituito: string  
  
## <a name="debugging-intellisense-extensions"></a>Debug delle estensioni di IntelliSense  
 È possibile eseguire il debug delle estensioni, ma è possibile usare la [intellisense oggetto](#intellisenseObject) funzione per inviare informazioni alla finestra di Output di Visual Studio. Per un esempio che illustra come usare questa funzione, vedere [invio di messaggi nella finestra di Output](#Logging) più avanti in questo argomento. Per `logMessage` per funzionare, almeno un gestore eventi deve essere registrato in un'estensione.  
  
## <a name="CodeExamples"></a> Esempi di codice  
 In questa sezione include esempi di codice che illustrano come usare l'API di estendibilità di IntelliSense. Esistono anche altri modi per usare queste API. Per altri esempi, vedere i seguenti file nei \\ \\ *il percorso di installazione di Visual Studio*\JavaScript\References cartella. Si siano lavorando gli esempi usati dal servizio di linguaggio JavaScript.  
  
- underscoreFilter.js. Questo codice consente di nascondere i membri privati da IntelliSense. Include i gestori eventi per il `statementcompletion` evento.  
  
- showPlainComments.js. Questo codice fornisce il supporto IntelliSense per i commenti standard. Include i gestori eventi per il `signaturehelp` e `statementcompletionhint` eventi.  
  
### <a name="Annotations"></a> Aggiunta di annotazioni di IntelliSense  
 La procedura seguente viene illustrato come fornire il supporto di documentazione di IntelliSense per una libreria di terze parti senza modificare direttamente la libreria. A tale scopo, è possibile usare `intellisense.annotate` in un'estensione.  
  
 Per eseguire l'esempio, è necessario che i seguenti file JavaScript siano disponibili nel progetto:  
  
- demoLib.js, vale a dire un file di progetto che rappresenta una libreria di terze parti.  
  
- demoLib.intellisense.js, che corrisponde all'estensione di IntelliSense. Questo file non deve essere incluso nel progetto, ma deve trovarsi nella stessa cartella di exampleLib.js.  
  
- appCode.js, ossia un file di progetto che rappresenta il codice dell'applicazione.  
  
##### <a name="to-add-an-intellisense-annotation"></a>Per aggiungere un'annotazione di IntelliSense  
  
1. Aggiungere il codice seguente a demoLib.js.  
  
    ```javascript  
    function someFunc(a) { };  
    var rectangle;  
  
    ```  
  
2. Aggiungere il codice seguente a demoLib.intellisense.js.  
  
    ```javascript  
    intellisense.annotate(someFunc, function (a) {  
        /// <signature>  
        /// <summary>Description of someFunc</summary>  
        /// <param name="a">Param a</param>  
        /// </signature>  
    });  
  
    intellisense.annotate(window, {  
        // This is a comment on a global variable named rectangle.  
        rectangle: undefined  
    });  
    ```  
  
3. Aggiungere la seguente direttiva di riferimento come prima riga in appCode.js. Il percorso usato in questo contesto indica che i file JavaScript sono nella stessa cartella.  
  
    ```javascript  
    /// <reference path="demoLib.js" />  
  
    ```  
  
4. In appCode.js, digitare il codice riportato di seguito. Si noterà i commenti della documentazione XML nell'estensione visualizzati come le informazioni sul parametro di IntelliSense.  
  
     ![Esempio che illustra l'uso di IntelliSense. annotate](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")  
  
5. In appCode.js, digitare il codice riportato di seguito. Durante la digitazione, scoprirai i commenti standard nell'estensione visualizzati come informazioni rapide di IntelliSense.  
  
     ![Esempio che illustra l'uso di IntelliSense. annotate](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")  
  
### <a name="Logging"></a> L'invio di messaggi nella finestra di Output  
 La procedura seguente illustra come inviare messaggi alla finestra di Output. È possibile inviare i messaggi per facilitare il debug delle estensioni IntelliSense.  
  
 Per eseguire l'esempio, è necessario che i seguenti file JavaScript siano disponibili nel progetto:  
  
- exampleLib.js, vale a dire un file di progetto che rappresenta una libreria di terze parti.  
  
- exampleLib.intellisense.js, che corrisponde all'estensione di IntelliSense. Questo file non deve essere incluso nel progetto, ma deve trovarsi nella stessa cartella di exampleLib.js.  
  
- appCode.js, ossia un file di progetto che rappresenta il codice dell'applicazione.  
  
##### <a name="to-send-a-message-to-the-output-window"></a>Per inviare un messaggio nella finestra di Output  
  
1. Aggiungere il codice seguente a exampleLib.js.  
  
    ```javascript  
    var someVar = {  
        a: 1,  
        b: 'hello'  
    };  
    ```  
  
2. Aggiungere il codice seguente a exampleLib.intellisense.js.  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        // Prints out statement completion info: Either (1) the member   
        // list, if the trigger character was typed, or (2) the   
        // statement completion identifiers.  
        // e.target represents the object left of the trigger character.  
        intellisense.logMessage(  
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');  
  
        // Prints out all statement completion items.  
        e.items.forEach(function (item) {  
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);  
        });  
    });  
    ```  
  
3. Aggiungere la seguente direttiva di riferimento come prima riga in appCode.js. Il percorso usato in questo contesto indica che i file JavaScript sono nella stessa cartella.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4. Nella finestra di Output, scegli **JavaScript Language Service** nel **Mostra output di** elenco. (Per visualizzare la finestra di Output, selezionare **Output** dal menu Visualizza.)  
  
5. In appCode.js, digitare il codice riportato di seguito. Mentre si digita, la finestra di Output Mostra messaggi dal servizio di linguaggio. Il primo messaggio nella finestra di Output indica che è stato richiesto il completamento delle istruzioni per l'ambito corrente.  
  
    ```javascript  
    some  
    ```  
  
     Di seguito è una visualizzazione parziale dell'output che verrà visualizzato.  
  
    ```scr  
    03:16:14.3113: statement completion for current scope requested  
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined  
  
    …  
    ```  
  
6. Scegliere il **Cancella tutto** pulsante nella finestra di Output.  
  
7. Digitare il codice seguente. Il primo messaggio nella finestra di output indica che è stato richiesto un elenco di membri.  
  
    ```javascript  
    someVar.  
    ```  
  
     Di seguito è una visualizzazione parziale dell'output che verrà visualizzato:  
  
    ```scr  
    03:17:43.4032: member list requested, target: someVar  
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1  
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello  
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:  
  
    …  
    ```  
  
### <a name="Icons"></a> Modificare le icone di IntelliSense  
 La procedura seguente viene illustrato come modificare le icone visualizzate da IntelliSense per impostazione predefinita. Questo potrebbe essere utile quando si forniscono informazioni di IntelliSense su concetti specifici di libreria, ad esempio gli spazi dei nomi, classi, interfacce ed enumerazioni.  
  
 Per i valori di icona disponibili, vedere <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>.  
  
 Per eseguire l'esempio, è necessario che i seguenti file JavaScript siano disponibili nel progetto:  
  
- exampleLib.js, ovvero un progetto di libreria represens una terza parte del file.  
  
- exampleLib.intellisense.js, che corrisponde all'estensione di IntelliSense. Questo file non deve essere incluso nel progetto, ma deve trovarsi nella stessa cartella di exampleLib.js.  
  
- appCode.js, ossia un file di progetto che rappresenta il codice dell'applicazione.  
  
##### <a name="to-change-the-icons"></a>Per modificare le icone  
  
1. Aggiungere il codice seguente a exampleLib.js.  
  
    ```javascript  
    function Namespace(name) {  
        this._isNamespace = true;  
        window[name] = this;  
    };  
  
    function Enum(values) {  
        var e = Object.create(values);  
        e._isEnum = true;  
        return e;  
    };  
  
    var SomeNamespace = new Namespace('SomeNamespace');  
    // A constructor function is considered a class.  
    SomeNamespace.SomeClass1 = function () { }  
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });  
    ```  
  
2. Aggiungere il codice seguente a exampleLib.intellisense.js.  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        e.items.forEach(function (item) {  
            // Detect a namespace by using the _isNamespace flag.  
            if (item.value && item.value._isNamespace) {  
                item.glyph = 'vs:GlyphGroupNamespace';  
                }  
  
            if (item.parentObject && item.parentObject._isNamespace) {  
                // The item is a member of a namespace.   
  
                // All constructor functions that are part of a namespace   
                // are considered classes.   
                // A constructor function starts with  
                // an uppercase letter by convention.    
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()   
                    == item.name[0])) {  
                    item.glyph = 'vs:GlyphGroupClass';  
                }  
  
                // Detect an enumeration by using the _isEnum flag.  
                if (item.value && item.value._isEnum) {  
                    item.glyph = 'vs:GlyphGroupEnum';  
                }  
            }  
        });  
    });  
  
    intellisense.addEventListener('statementcompletionhint', function (e) {  
        if (e.completionItem.value) {  
            if (e.completionItem.value._isNamespace) {  
                e.symbolHelp.symbolDisplayType = 'Namespace';  
            }  
            if (e.completionItem.value._isEnum) {  
                e.symbolHelp.symbolDisplayType = 'Enum';  
            }  
        }  
    });  
    ```  
  
3. Aggiungere la seguente direttiva di riferimento come prima riga in appCode.js. Il percorso usato in questo contesto indica che i file JavaScript sono nella stessa cartella.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4. In appCode.js, digitare il codice riportato di seguito. Durante la digitazione, si noterà che l'icona per lo spazio dei nomi è stato modificato da "{}", come viene usato in c#.  
  
     ![Esempio che illustra l'uso della proprietà del glifo](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")  
  
5. In appCode.js, digitare il codice riportato di seguito. Durante la digitazione, si noterà una nuova icona di enumerazione per il membro Enum1 e una nuova icona di classe per il membro SomeClass1.  
  
     ![Esempio che illustra l'uso della proprietà del glifo](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")  
  
### <a name="Overriding"></a> Come evitare gli effetti di runtime sui risultati di IntelliSense  
 Il servizio JavaScript language service viene eseguito il codice per fornire in modo dinamico le informazioni di IntelliSense. Di conseguenza, comportamento di run-time in alcuni casi può interferire con i risultati desiderati. La procedura seguente illustra come eseguire l'override dei risultati di IntelliSense quando il comportamento in fase di esecuzione genera IntelliSense non corretto.  
  
 Per eseguire l'esempio, è necessario che i seguenti file JavaScript siano disponibili nel progetto:  
  
- exampleLib.js, vale a dire un file di progetto che rappresenta una libreria di terze parti.  
  
- exampleLib.intellisense.js, che corrisponde all'estensione di IntelliSense. Questo file non deve essere incluso nel progetto, ma deve trovarsi nella stessa cartella di exampleLib.js.  
  
- appCode.js, ossia un file di progetto che rappresenta il codice dell'applicazione.  
  
##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>Per evitare effetti in fase di esecuzione sui risultati di IntelliSense  
  
1. Aggiungere il codice seguente a exampleLib.js.  
  
    ```javascript  
    function after(count, func) {  
        return function () {  
            if (--times < 1) {  
                return func.apply(this, arguments);  
            }  
        };  
    };  
    ```  
  
     Nel codice precedente, la funzione con wrapping Ignora chiamate iniziale, in base al valore di `count`e non restituisce risultati.  
  
2. Aggiungere la seguente direttiva di riferimento come prima riga in appCode.js. Il percorso usato in questo contesto indica che i file JavaScript sono nella stessa cartella.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
3. In appCode.js, digitare il codice riportato di seguito. Verrà visualizzato l'elenco di identificatore invece di IntelliSense perché la funzione con wrapping non viene mai chiamata, il che significa che il `throttled` la funzione non restituisce alcun risultato.  
  
     ![Esempio di override dei risultati di intellisense](../ide/media/js-intellisense-override.png "js_intellisense_override")  
  
4. Aggiungere il codice seguente a exampleLib.intellisense.js. Si modificherà il comportamento in fase di progettazione in modo che venga visualizzato IntelliSense per la funzione con wrapping, come previsto.  
  
    ```javascript  
    window.after = function (count, func) {  
        // Just return func.   
        return func;  
    };  
    ```  
  
5. In appcode. js, testare i risultati digitando lo stesso codice che è stato digitato in precedenza. Questa volta, IntelliSense offre le informazioni desiderate.  
  
     ![Esempio di override dei risultati di IntelliSense](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")  
  
## <a name="see-also"></a>Vedere anche  
 [IntelliSense per JavaScript](../ide/javascript-intellisense.md)   
 [Completamento delle istruzioni per gli identificativi](../ide/statement-completion-for-identifiers.md)
