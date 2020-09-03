---
title: Estensione di IntelliSense per JavaScript | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf16b6fdc307e11875f30cfad6e4bb35580b0b04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665757"
---
# <a name="extending-javascript-intellisense"></a>Estensione di IntelliSense in JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La funzionalità Extensibility JavaScript IntelliSense consente di personalizzare i risultati di IntelliSense nell'editor JavaScript per le librerie di terze parti. Questo può migliorare l'esperienza degli sviluppatori che usano queste librerie.

 Il servizio di linguaggio JavaScript fornisce le funzionalità di IntelliSense per le librerie JavaScript di terze parti che vengono aggiunte a un progetto. Per la maggior parte delle librerie, il completamento delle istruzioni viene fornito automaticamente dal servizio di linguaggio. Nella figura seguente viene illustrato un esempio di completamento delle istruzioni:

 ![Esempio di completamento istruzioni](../ide/media/js-intellisense-completion.png "js_intellisense_completion")

 Se nella libreria sono incluse descrizioni di variabili, funzioni e oggetti nei tag di commento JavaScript standard (//), per impostazione predefinita si traggono automaticamente vantaggio dalle funzionalità di estensibilità IntelliSense, che forniscono informazioni descrittive in una finestra popup a destra degli elementi in un elenco di completamento o quando si digita la parentesi di apertura in una chiamata di funzione. I commenti nella casella popup contengono la descrizione del membro. Nell'esempio seguente viene illustrata la casella popup per un elenco di completamento.

 ![Esempio di una finestra popup di informazioni rapide&#45;](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")

 Per migliorare ulteriormente l'esperienza dello sviluppatore, è possibile fornire informazioni sul tipo per gli sviluppatori nella casella popup. È possibile fornire informazioni sui tipi usando commenti relativi alla [documentazione XML](../ide/xml-documentation-comments-javascript.md) JavaScript anziché i tag di commento standard. I commenti relativi alla documentazione XML vengono aggiunti utilizzando tag di commento a barra tripla (///) e un set definito di elementi XML.

 In alternativa, è possibile fornire informazioni sul tipo usando l'estensibilità IntelliSense per JavaScript. Questa funzionalità consente di personalizzare i risultati IntelliSense creando estensioni JavaScript e aggiungendole al contesto di script. Nell'estensione, che è un file JavaScript, si sottoscrivono gli eventi esposti dall' `intellisense` oggetto del servizio di linguaggio. L'estendibilità IntelliSense per JavaScript è la soluzione preferita per le librerie se un modello di comportamento nella libreria impedisce al servizio di linguaggio JavaScript di fornire il livello desiderato di supporto IntelliSense e se è necessaria anche un'alternativa ai commenti della documentazione XML dichiarativa. Personalizzando i risultati di IntelliSense, è possibile creare un'esperienza IntelliSense di prima classe, indipendentemente da eventuali modelli di comportamento che potrebbero limitare le funzionalità predefinite del servizio di linguaggio. Per altre informazioni, vedere [Completamento delle istruzioni per gli identificativi](../ide/statement-completion-for-identifiers.md).

## <a name="adding-an-extension-to-the-script-context"></a>Aggiunta di un'estensione al contesto di script
 Per eseguire un'estensione di IntelliSense, è necessario aggiungerla al contesto di script corrente. L'estensione può essere aggiunta automaticamente al contesto di script dal meccanismo di individuazione automatica oppure è possibile aggiungere l'estensione al contesto dello script manualmente usando i gruppi di riferimento o la direttiva di riferimento.

 Il meccanismo di individuazione automatica consente al servizio di linguaggio di trovare automaticamente le estensioni che seguono la convenzione di denominazione dei file *libraryname*.intellisense.js e che si trovano nella stessa directory della libreria a cui viene applicata l'estensione. È ad esempio jQuery.intellisense.js un'estensione valida per la libreria jQuery. Per le estensioni jQuery più restrittive, è possibile usare nomi di file quali jQuery-1.7.1.intellisense.js (un'estensione specifica della versione) o jQuery.ui.intellisense.js (estensione per una libreria jQuery con ambito). La versione più restrittiva dell'estensione viene utilizzata se viene trovata più di un'estensione per una determinata libreria.

 Se si desidera utilizzare l'estensione per tutti i file di progetto JavaScript, è possibile scegliere di aggiungere l'estensione a un gruppo di riferimenti. Esistono diversi tipi di gruppi di riferimento, ovvero quelli che includono riferimenti impliciti e quelli che includono riferimenti a thread di lavoro dedicati. Per aggiungere un'estensione, in genere è necessario aggiungere il file come gruppo di riferimenti implicito **(implicito (Windows)**, **implicito (Web)**. I riferimenti impliciti rientrano nell'ambito per ogni file con estensione js aperto nell'editor di codice. Quando si usa questo metodo, è necessario aggiungere l'estensione e il file che l'estensione sta integrando.

 Utilizzare la pagina **IntelliSense** della finestra di dialogo **Opzioni** per aggiungere un'estensione come gruppo di riferimento. Per accedere alla pagina **IntelliSense** , scegliere **strumenti**, **Opzioni** nella barra dei menu, quindi scegliere Editor di **testo**, **JavaScript**, **IntelliSense**, **riferimenti**. Per ulteriori informazioni sui gruppi di riferimento, vedere [JavaScript IntelliSense](../ide/javascript-intellisense.md) and [options, text editor, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

 Se si desidera utilizzare l'estensione per un set di file specifico, utilizzare una direttiva di riferimento. Quando si usa questo metodo, è necessario fare riferimento sia all'estensione che al file che l'estensione sta integrando. Per informazioni sull'uso della direttiva Reference, vedere [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="handling-intellisense-events"></a>Gestione degli eventi IntelliSense
 La funzionalità di estendibilità consente di personalizzare i risultati di IntelliSense sottoscrivendo eventi come l' `statementcompletion` evento dell'oggetto servizio di linguaggio `intellisense` . Nell'esempio seguente viene illustrata un'estensione semplice usata dal servizio di linguaggio per nascondere i membri che iniziano con un carattere di sottolineatura dal completamento delle istruzioni. Questo codice è contenuto in underscorefilter.js e si trova nella \\ \\ cartella \JavaScript\References del *percorso di installazione di Visual Studio*.

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

 Nel codice precedente, l'estensione controlla la proprietà [TargetName](#TargetName) e le proprietà di [destinazione](#Target) dell' `statementcompletion` oggetto evento per escludere gli oggetti, ad esempio `this` e `window` , e per assicurarsi che sia possibile identificare un elenco di completamento di istruzioni valido. Se è possibile identificare un elenco di completamento, l'estensione aggiorna la raccolta di [proprietà degli elementi](#Items) di completamento dell'istruzione filtrando i membri che iniziano con un carattere di sottolineatura.

 Per altri esempi, vedere il \\ \\ *percorso di installazione di Visual Studio*\JavaScript\References cartella. Il file showPlainComments.js in questa cartella fornisce esempi di utilizzo di altri eventi per fornire il supporto IntelliSense predefinito per i tag di commento JavaScript standard (//). Analogamente a underscorefilter.js, showPlainComments.js è già disponibile come estensione funzionante ed è possibile visualizzare le informazioni di IntelliSense risultanti quando si utilizzano tag di commento nel codice per variabili, funzioni e oggetti. Per altri esempi, vedere [esempi di codice](#CodeExamples).

> [!WARNING]
> Se si modificano i file di estensione inclusi in Visual Studio, è possibile disabilitare JavaScript IntelliSense o la funzionalità supportata dall'estensione.

 Nel codice dell'estensione è possibile creare gestori per i tipi di eventi seguenti utilizzando `addEventListener` :

- `statementcompletion`, che aggiunge un gestore per un evento di completamento dell'istruzione. Il completamento delle istruzioni fornisce un elenco di membri per un tipo particolare visualizzato dopo avere digitato un carattere speciale, ad esempio un punto (.), o un elenco di identificatori visualizzato durante la digitazione o quando si preme CTRL + J. Il gestore riceve un oggetto evento di tipo `CompletionEvent` , che supporta i membri seguenti: [proprietà Items](#Items), [target Property](#Target), [TargetName Property](#TargetName)e [scope Property](#Scope).

- `signaturehelp`, che aggiunge un gestore per le informazioni sul parametro IntelliSense. Le informazioni sui parametri forniscono informazioni sul numero, i nomi e i tipi di parametri richiesti da una funzione. Il gestore riceve un oggetto evento di tipo `SignatureHelpEvent` , che supporta i membri seguenti: [proprietà di destinazione](#Target), [Proprietà ParentObject](#ParentObject), [Proprietà functionComments](#FunctionComments), [Proprietà functionHelp](#FunctionHelp).

- `statementcompletionhint`, che aggiunge un gestore per informazioni rapide di IntelliSense. Nella casella popup informazioni rapide viene visualizzata la dichiarazione completa per gli identificatori nel codice. Il gestore riceve un oggetto evento di tipo `CompletionHintEvent` , che supporta i membri seguenti: [completionItem](#CompletionItem)e la [Proprietà symbolHelp](#SymbolHelp).

  Per esempi che illustrano le funzionalità di IntelliSense, ad esempio il completamento delle istruzioni, le informazioni sui parametri e le informazioni rapide, vedere [utilizzo di IntelliSense](../ide/using-intellisense.md).

> [!NOTE]
> In JavaScript, informazioni rapide si riferisce alla casella popup visualizzata a destra di un elenco di completamento. Non è possibile richiamare manualmente le informazioni rapide.

## <a name="intellisense-object"></a><a name="intellisenseObject"></a> Oggetto IntelliSense
 Nella tabella seguente vengono illustrate le funzioni disponibili per l' `intellisense` oggetto. L' `intellisense` oggetto è disponibile solo in fase di progettazione.

|Funzione|Descrizione|
|--------------|-----------------|
|`addEventListener(type, handler);`|Aggiunge un gestore eventi per un evento IntelliSense.<br /><br /> `type` è un valore stringa. I valori validi includono `statementcompletion`, `signaturehelp` e `statementcompletionhint`.<br /><br /> `handler` è una funzione del gestore eventi che riceve un oggetto evento di uno dei tipi seguenti:<br /><br /> -   `CompletionEvent`, utilizzato per l' `statementcompletion` evento.<br />-   `SignatureHelpEvent`, utilizzato per l' `signaturehelp` evento.<br />-   `CompletionHintEvent`, utilizzato per l' `statementcompletionhint` evento.<br /><br /> Per esempi che usano questa funzione, vedere [esempi di codice](#CodeExamples).|
|`annotate(obj, doc);`|Specifica la documentazione per un oggetto copiando i commenti della documentazione da un oggetto a un altro oggetto.<br /><br /> `obj` Specifica l'oggetto in cui copiare la documentazione.<br /><br /> `doc` Specifica l'oggetto da cui copiare la documentazione.<br /><br /> Per un esempio in cui viene illustrato come usare questa funzione, vedere [aggiunta di annotazioni IntelliSense](#Annotations).|
|`getFunctionComments(func);`|Restituisce i commenti per una funzione specificata.<br /><br /> `func` Specifica la funzione per la quale vengono restituiti i commenti.<br /><br /> È possibile impostare il `func` parametro utilizzando `completionItem.value` .<br /><br /> L' `functionComments` oggetto restituito include i membri seguenti: `above` , `inside` e `paramComment` . Per ulteriori informazioni, vedere la proprietà [FunctionComments Property](#FunctionComments) .<br /><br /> `getFunctionComments` può essere chiamato solo dall'interno di uno dei gestori eventi registrati da `addEventListener` .<br /><br /> Per un esempio in cui viene illustrato come usare questa funzione, vedere il \\ \\ *percorso di installazione di Visual Studio*\JavaScript\References\showPlainComments.js.|
|`logMessage(msg);`|Invia messaggi di diagnostica alla finestra di output.<br /><br /> `msg` stringa che contiene il messaggio.<br /><br /> Per un esempio in cui viene illustrato come usare questa funzione, vedere [invio di messaggi al finestra di output](#Logging).|
|`nullWithCompletionsOf(value);`|Restituisce un valore null speciale per il quale l'elenco di completamento è determinato dall'oggetto passato nel `value` parametro.<br /><br /> `value` determina l'elenco di completamento per il valore restituito. `value` può essere qualsiasi tipo.<br /><br /> Il valore restituito null viene considerato null in fase di progettazione, ma l'elenco di completamento del valore restituito è uguale all'elenco di completamento per il `value` parametro.<br /><br /> Un utilizzo per questa funzione è fornire a IntelliSense un valore restituito quando il tipo restituito è stimabile in fase di esecuzione, ma il valore restituito è in fase di `null` progettazione.|
|`redirectDefinition(func, definition);`|Indica a IntelliSense di usare la funzione di definizione fornita anziché la funzione Func originale quando è richiesta la guida del parametro o **Vai a definizione** .<br /><br /> `func` Specifica la funzione di destinazione.<br /><br /> `definition` Specifica la funzione da usare al posto della funzione di destinazione per le informazioni sui parametri e **Vai a definizione**.|
|`setCallContext(func, thisArg);`|Imposta il contesto di chiamata o l'ambito per la funzione specificata.<br /><br /> `func` Specifica la funzione per la quale impostare l'ambito.<br /><br /> `thisArg` valore letterale dell'oggetto a cui la `this` parola chiave può fare riferimento, che specifica il nuovo ambito per il membro. È possibile includere argomenti da passare in questo parametro, ad esempio `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` fornisce un comportamento simile a `Function.prototype.bind` , ad eccezione del fatto che viene utilizzato solo per il supporto IntelliSense della fase di progettazione. È possibile usare `setCallContext` per impostare l'ambito della funzione se è necessario simulare una chiamata a codice che non è altrimenti raggiungibile, in modo che quando si chiama la funzione, la chiamata di funzione includerà l'ambito e gli argomenti corretti.|
|`undefinedWithCompletionsOf(value);`|Restituisce un valore speciale non definito per il quale l'elenco di completamento è determinato dall'oggetto passato nel `value` parametro.<br /><br /> `value` determina l'elenco di completamento per il valore restituito. `value` può essere qualsiasi tipo.<br /><br /> Il valore restituito non definito viene considerato come non definito in fase di progettazione, ma l'elenco di completamento del valore restituito è uguale all'elenco di completamento per il `value` parametro.<br /><br /> Un utilizzo per questa funzione è fornire a IntelliSense un valore restituito quando il tipo restituito è stimabile in fase di esecuzione, ma il valore restituito non è definito in fase di progettazione.|
|`version()`|Restituisce la versione di Visual Studio.|

## <a name="event-members"></a>Membri evento
 Nelle sezioni seguenti vengono descritti i membri esposti nell'oggetto evento per gli eventi seguenti: `statementcompletion` , `signaturehelp` e `statementcompletionhint` .

### <a name="completionitem-property"></a><a name="CompletionItem"></a> Proprietà completionItem
 Restituisce l'identificatore, noto come elemento di completamento, per il quale è richiesta una casella popup per informazioni rapide. Questa proprietà è disponibile per l' `statementcompletionhint` oggetto evento e per la proprietà [Items](#Items) della proprietà dell' `statementcompletion` oggetto evento.

 Valore restituito: `completionItem` oggetto

 Di seguito sono riportati i membri dell' `completionItem` oggetto:

- `name`. Lettura/scrittura se utilizzata nella `items` raccolta; in caso contrario, in sola lettura. Restituisce una stringa che identifica l'elemento di completamento.

- `kind`. Lettura/scrittura se utilizzata nella `items` raccolta; in caso contrario, in sola lettura. Restituisce una stringa che rappresenta il tipo di elemento di completamento. I valori possibili sono metodo, campo, proprietà, parametro, variabile e riservato.

- `glyph`. Lettura/scrittura se utilizzata nella `items` raccolta; in caso contrario, in sola lettura. Restituisce una stringa che rappresenta un'icona visualizzata nell'elenco di completamento. I valori possibili per `glyph` usano il formato seguente: vs:*GlyphType*, dove *GlyphType* corrisponde ai membri indipendenti dal linguaggio nell' <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> enumerazione. Ad esempio, `vs:GlyphGroupMethod` è un valore possibile per `glyph` . Quando `glyph` non è impostato, la `kind` proprietà determina l'icona predefinita.

- `parentObject`. Sola lettura. Restituisce l'oggetto padre.

- `value`. Sola lettura. Restituisce un oggetto che rappresenta il valore dell'elemento di completamento.

- `comments`. Sola lettura. Restituisce una stringa che contiene i commenti sopra il campo o la variabile.

- `scope`. Sola lettura. Restituisce l'ambito dell'elemento di completamento. I valori possibili sono Global, local, Parameter e member.

### <a name="items-property"></a><a name="Items"></a> Items (proprietà)
 Ottiene o imposta la matrice di elementi di completamento dell'istruzione. Ogni elemento nella matrice è un oggetto [Proprietà completionItem](#CompletionItem) . La `items` proprietà è disponibile per l' `statementcompletion` oggetto evento.

 Valore restituito: Array

### <a name="functioncomments-property"></a><a name="FunctionComments"></a> Proprietà functionComments
 Restituisce i commenti per la funzione. Questa proprietà è disponibile per l' `signaturehelp` oggetto evento.

 Valore restituito: `comments` oggetto

 Di seguito sono riportati i membri dell' `comments` oggetto:

- `above`. Restituisce i commenti sopra la funzione.

- `inside`. Restituisce i commenti all'interno della funzione, in genere nel formato VSDoc.

- `paramComments`. Restituisce una matrice che rappresenta i commenti per ogni parametro nella funzione. I membri della matrice includono:

  - `name`. Restituisce una stringa che rappresenta il nome del parametro.

  - `comment`. Restituisce una stringa che contiene il commento sul parametro.

### <a name="functionhelp-property"></a><a name="FunctionHelp"></a> Proprietà functionHelp
 Restituisce la guida per la funzione. Questa proprietà è disponibile per l' `signaturehelp` oggetto evento.

 Valore restituito: `functionHelp` oggetto

 Di seguito sono riportati i membri dell' `functionHelp` oggetto:

- `functionName`. Proprietà di lettura/scrittura. Restituisce una stringa che contiene il nome della funzione.

- `signatures`. Proprietà di lettura/scrittura. Ottiene o imposta la matrice di firme di funzione. Ogni elemento nella matrice è un `signature` oggetto. Alcune `signature` proprietà, ad esempio `locid` , corrispondono agli attributi comuni di commenti relativi alla [documentazione XML](../ide/xml-documentation-comments-javascript.md) .

  I membri dell' `signature` oggetto includono:

  - `description`. Proprietà di lettura/scrittura. Restituisce una stringa che descrive la funzione.

  - `locid`. Proprietà di lettura/scrittura. Restituisce un identificatore di stringa che contiene informazioni di localizzazione sulla funzione.

  - `helpKeyword`. Proprietà di lettura/scrittura. Restituisce una stringa che contiene la parola chiave della guida.

  - `externalFile`. Proprietà di lettura/scrittura. Restituisce una stringa che rappresenta il file che contiene l'ID del membro.

  - `externalid`. Proprietà di lettura/scrittura. Restituisce una stringa che rappresenta l'ID del membro della funzione.

  - `params`. Proprietà di lettura/scrittura. Ottiene o imposta la matrice di parametri per la funzione. Ogni elemento nella matrice parameters è un `parameter` oggetto che dispone di proprietà corrispondenti agli attributi seguenti dell' [\<param>](../ide/param-javascript.md) elemento:

    - `name`. Proprietà di lettura/scrittura. Restituisce una stringa che rappresenta il nome del parametro.

    - `type`. Proprietà di lettura/scrittura. Restituisce una stringa che rappresenta il tipo di parametro.

    - `elementType`. Proprietà di lettura/scrittura. Se il tipo è `Array` , restituisce una stringa che rappresenta il tipo degli elementi nella matrice.

    - `description`. Proprietà di lettura/scrittura. Restituisce una stringa che descrive il parametro.

    - `locid`. Proprietà di lettura/scrittura. Restituisce un identificatore di stringa che contiene informazioni di localizzazione sulla funzione.

    - `optional`. Proprietà di lettura/scrittura. Restituisce una stringa che indica se il parametro è facoltativo. `true` indica che il parametro è facoltativo. `false` indica che non lo è.

  - `returnValue`. Proprietà di lettura/scrittura. Ottiene o imposta un oggetto valore restituito con proprietà che corrispondono ai seguenti attributi dell' [\<returns>](../ide/returns-javascript.md) elemento:

    - `type`. Proprietà di lettura/scrittura. Restituisce una stringa che rappresenta il tipo restituito.

    - `elementType`. Proprietà di lettura/scrittura. Se il tipo è `Array` , restituisce una stringa che rappresenta il tipo degli elementi nella matrice.

    - `description`. Proprietà di lettura/scrittura. Restituisce una stringa che descrive il valore restituito.

    - `locid`. Proprietà di lettura/scrittura. Restituisce un identificatore di stringa che contiene informazioni di localizzazione sulla funzione.

    - `helpKeyword`. Proprietà di lettura/scrittura. Restituisce una stringa che contiene la parola chiave della guida.

    - `externalFile`. Proprietà di lettura/scrittura. Restituisce una stringa che rappresenta il file che contiene l'ID del membro.

    - `externalid`. Proprietà di lettura/scrittura. Restituisce una stringa che rappresenta l'ID del membro della funzione.

### <a name="parentobject-property"></a><a name="ParentObject"></a> Proprietà parentObject
 Restituisce l'oggetto padre di una funzione membro. Per, ad esempio `document.getElementByID` , `parentObject` restituisce l' `document` oggetto. Questa proprietà è disponibile per l' `signaturehelp` oggetto evento.

 Valore restituito: oggetto

### <a name="target-property"></a><a name="Target"></a> Proprietà di destinazione
 Restituisce un oggetto che rappresenta l'elemento a sinistra del carattere del trigger, che è un punto (.). Per le funzioni, `target` restituisce la funzione per la quale sono richieste le informazioni sul parametro. Questa proprietà è disponibile per gli `statementcompletion` `signaturehelp` oggetti evento e.

 Valore restituito: oggetto

### <a name="targetname-property"></a><a name="TargetName"></a> Proprietà TargetName
 Restituisce una stringa che rappresenta la destinazione. Ad esempio, per "this.", `targetName` restituisce "This". Per "A. B" (quando il cursore si trova dopo "B"), `targetName` restituisce "b". Questa proprietà è disponibile per l' `statementcompletion` oggetto evento.

 Valore restituito: String

### <a name="symbolhelp-property"></a><a name="SymbolHelp"></a> Proprietà symbolHelp
 Restituisce l'elemento di completamento per il quale viene richiesta una casella popup per informazioni rapide. Questa proprietà è disponibile per l' `statementcompletionhint` oggetto evento.

 Valore restituito: `symbolHelp` Object.

 Alcune proprietà dell' `symbolHelp` oggetto, ad esempio `locid` , corrispondono agli attributi comuni di commenti relativi alla [documentazione XML](../ide/xml-documentation-comments-javascript.md) .

 Di seguito sono riportati i membri dell' `symbolHelp` oggetto:

- `name`. Proprietà di lettura/scrittura. Restituisce una stringa che contiene il nome dell'identificatore.

- `symbolType`. Proprietà di lettura/scrittura. Restituisce una stringa che rappresenta il tipo di simbolo. I valori possibili includono Unknown, Boolean, Number, String, Object, Function, array, date e Regex.

- `symbolDisplayType`. Proprietà di lettura/scrittura. Restituisce una stringa che contiene il nome del tipo da visualizzare. Se `symbolDisplayType` non è impostato, `symbolType` viene utilizzato.

- `elementType`. Proprietà di lettura/scrittura. Se `symbolType` è `Array` , restituisce una stringa che rappresenta il tipo degli elementi nella matrice.

- `scope`. Proprietà di lettura/scrittura. Restituisce una stringa che rappresenta l'ambito del simbolo. I valori possibili sono Global, local, Parameter e member.

- `description`. Proprietà di lettura/scrittura. Restituisce una stringa che contiene una descrizione del simbolo.

- `locid`. Proprietà di lettura/scrittura. Restituisce un identificatore di stringa che contiene informazioni di localizzazione sul simbolo.

- `helpKeyword`. Proprietà di lettura/scrittura. Restituisce una stringa che contiene la parola chiave della guida.

- `externalFile`. Proprietà di lettura/scrittura. Restituisce una stringa che rappresenta il file che contiene l'ID del membro.

- `externalid`. Proprietà di lettura/scrittura. Restituisce una stringa che rappresenta l'ID del membro del simbolo.

- `functionHelp`. Proprietà di lettura/scrittura. Restituisce una [Proprietà functionHelp](#FunctionHelp)che può contenere informazioni quando la `symbolType` funzione è.

### <a name="scope-property"></a><a name="Scope"></a> Proprietà Scope
 Restituisce l'ambito di completamento dell'evento. I valori possibili per l'ambito di completamento sono Global e members. Questa proprietà è disponibile per l' `statementcompletion` oggetto evento.

 Valore restituito: String

## <a name="debugging-intellisense-extensions"></a>Debug di estensioni IntelliSense
 Non è possibile eseguire il debug delle estensioni, ma è possibile usare la funzione dell' [oggetto IntelliSense](#intellisenseObject) per inviare informazioni alla finestra di output di Visual Studio. Per un esempio in cui viene illustrato come utilizzare questa funzione, vedere [invio di messaggi al finestra di output](#Logging) più avanti in questo argomento. Per il `logMessage` funzionamento di, almeno un gestore eventi deve essere registrato in un'estensione.

## <a name="code-examples"></a><a name="CodeExamples"></a> Esempi di codice
 Questa sezione include esempi di codice che illustrano come usare le API di estendibilità di IntelliSense. Sono disponibili anche altri modi per usare queste API. Per altri esempi, vedere i file seguenti nella \\ \\ cartella *percorso di installazione di Visual Studio*\JavaScript\References. Questi sono esempi di funzionamento usati dal servizio di linguaggio JavaScript.

- underscoreFilter.js. Questo codice nasconde i membri privati da IntelliSense. Include i gestori eventi per l' `statementcompletion` evento.

- showPlainComments.js. Questo codice fornisce supporto IntelliSense per i commenti standard. Include i gestori eventi per gli `signaturehelp` eventi e `statementcompletionhint` .

### <a name="adding-intellisense-annotations"></a><a name="Annotations"></a> Aggiunta di annotazioni IntelliSense
 Nella procedura seguente viene illustrato come fornire supporto per la documentazione IntelliSense per una libreria di terze parti senza modificare direttamente la libreria. A tale scopo, è possibile usare `intellisense.annotate` in un'estensione.

 Per eseguire l'esempio, è necessario che i seguenti file JavaScript siano disponibili nel progetto:

- demoLib.js, ovvero un file di progetto che rappresenta una libreria di terze parti.

- demoLib.intellisense.js, ovvero l'estensione IntelliSense. Questo file non deve essere incluso nel progetto, ma deve trovarsi nella stessa cartella di exampleLib.js.

- appCode.js, ossia un file di progetto che rappresenta il codice dell'applicazione.

##### <a name="to-add-an-intellisense-annotation"></a>Per aggiungere un'annotazione IntelliSense

1. Aggiungere il codice seguente per demoLib.js.

    ```javascript
    function someFunc(a) { };
    var rectangle;

    ```

2. Aggiungere il codice seguente per demoLib.intellisense.js.

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

4. In appCode.js, digitare il codice riportato di seguito. I commenti della documentazione XML nell'estensione verranno visualizzati come informazioni sul parametro IntelliSense.

     ![Esempio che illustra l'uso di intellisense.annotate](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")

5. In appCode.js, digitare il codice riportato di seguito. Durante la digitazione, verranno visualizzati i commenti standard nell'estensione visualizzata come informazioni rapide di IntelliSense.

     ![Esempio che illustra l'uso di intellisense.annotate](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")

### <a name="sending-messages-to-the-output-window"></a><a name="Logging"></a> Invio di messaggi al Finestra di output
 Nella procedura riportata di seguito viene illustrato come inviare messaggi alla finestra output. È possibile inviare messaggi per facilitare il debug delle estensioni IntelliSense.

 Per eseguire l'esempio, è necessario che i seguenti file JavaScript siano disponibili nel progetto:

- exampleLib.js, ovvero un file di progetto che rappresenta una libreria di terze parti.

- exampleLib.intellisense.js, ovvero l'estensione IntelliSense. Questo file non deve essere incluso nel progetto, ma deve trovarsi nella stessa cartella di exampleLib.js.

- appCode.js, ossia un file di progetto che rappresenta il codice dell'applicazione.

##### <a name="to-send-a-message-to-the-output-window"></a>Per inviare un messaggio alla finestra di output

1. Aggiungere il codice seguente per exampleLib.js.

    ```javascript
    var someVar = {
        a: 1,
        b: 'hello'
    };
    ```

2. Aggiungere il codice seguente per exampleLib.intellisense.js.

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

4. Nella finestra output scegliere **JavaScript Language Service** nell'elenco **Mostra output da** . Per visualizzare la finestra output, scegliere **output** dal menu Visualizza.

5. In appCode.js, digitare il codice riportato di seguito. Durante la digitazione, nella finestra output vengono visualizzati i messaggi del servizio di linguaggio. Il primo messaggio nella finestra di output indica che è stato richiesto il completamento delle istruzioni per l'ambito corrente.

    ```javascript
    some
    ```

     Di seguito è riportata una visualizzazione parziale dell'output che dovrebbe essere visualizzato.

    ```scr
    03:16:14.3113: statement completion for current scope requested
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined

    …
    ```

6. Scegliere il pulsante **Cancella tutto** nella finestra output.

7. Digitare il codice seguente. Il primo messaggio nella finestra di output indica che è stato richiesto un elenco di membri.

    ```javascript
    someVar.
    ```

     Di seguito è riportata una visualizzazione parziale dell'output che dovrebbe essere visualizzato:

    ```scr
    03:17:43.4032: member list requested, target: someVar
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:

    …
    ```

### <a name="changing-the-intellisense-icons"></a><a name="Icons"></a> Modifica delle icone IntelliSense
 Nella procedura riportata di seguito viene illustrato come modificare le icone visualizzate da IntelliSense per impostazione predefinita. Questo può essere utile quando si forniscono informazioni IntelliSense su concetti specifici della libreria, ad esempio spazi dei nomi, classi, interfacce ed enumerazioni.

 Per i valori delle icone disponibili, vedere <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> .

 Per eseguire l'esempio, è necessario che i seguenti file JavaScript siano disponibili nel progetto:

- exampleLib.js, ovvero un file di progetto che represens una libreria di terze parti.

- exampleLib.intellisense.js, ovvero l'estensione IntelliSense. Questo file non deve essere incluso nel progetto, ma deve trovarsi nella stessa cartella di exampleLib.js.

- appCode.js, ossia un file di progetto che rappresenta il codice dell'applicazione.

##### <a name="to-change-the-icons"></a>Per modificare le icone

1. Aggiungere il codice seguente per exampleLib.js.

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

2. Aggiungere il codice seguente per exampleLib.intellisense.js.

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

4. In appCode.js, digitare il codice riportato di seguito. Durante la digitazione si noterà che l'icona per lo spazio dei nomi è cambiata in " {} ", come viene usato in C#.

     ![Esempio che illustra l'uso della proprietà del glifo](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")

5. In appCode.js, digitare il codice riportato di seguito. Durante la digitazione verrà visualizzata una nuova icona di enumerazione per il membro Enum1 e una nuova icona di classe per il membro SomeClass1.

     ![Esempio che illustra l'uso della proprietà del glifo](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")

### <a name="avoiding-run-time-effects-on-intellisense-results"></a><a name="Overriding"></a> Prevenzione degli effetti della fase di esecuzione sui risultati di IntelliSense
 Il servizio di linguaggio JavaScript esegue il codice per fornire in modo dinamico le informazioni di IntelliSense. Di conseguenza, il comportamento in fase di esecuzione può occasionalmente interferire con i risultati desiderati. Nella procedura seguente viene illustrato come eseguire l'override dei risultati di IntelliSense quando il comportamento in fase di esecuzione restituisce IntelliSense errato.

 Per eseguire l'esempio, è necessario che i seguenti file JavaScript siano disponibili nel progetto:

- exampleLib.js, ovvero un file di progetto che rappresenta una libreria di terze parti.

- exampleLib.intellisense.js, ovvero l'estensione IntelliSense. Questo file non deve essere incluso nel progetto, ma deve trovarsi nella stessa cartella di exampleLib.js.

- appCode.js, ossia un file di progetto che rappresenta il codice dell'applicazione.

##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>Per evitare effetti sulla fase di esecuzione sui risultati di IntelliSense

1. Aggiungere il codice seguente per exampleLib.js.

    ```javascript
    function after(count, func) {
        return function () {
            if (--times < 1) {
                return func.apply(this, arguments);
            }
        };
    };
    ```

     Nel codice precedente, la funzione di cui è stato eseguito il wrapper ignora le chiamate iniziali, in base al valore di `count` e non restituisce risultati.

2. Aggiungere la seguente direttiva di riferimento come prima riga in appCode.js. Il percorso usato in questo contesto indica che i file JavaScript sono nella stessa cartella.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

3. In appCode.js, digitare il codice riportato di seguito. L'elenco di identificatori viene visualizzato anziché IntelliSense perché la funzione di cui è stato eseguito il wrapper non viene mai chiamata, il che significa che la `throttled` funzione non restituisce alcun risultato.

     ![Esempio di override dei risultati di IntelliSense](../ide/media/js-intellisense-override.png "js_intellisense_override")

4. Aggiungere il codice seguente per exampleLib.intellisense.js. In questo modo verrà modificato il comportamento della fase di progettazione in modo che IntelliSense venga visualizzato per la funzione di cui è stato eseguito il Wrapped, come previsto.

    ```javascript
    window.after = function (count, func) {
        // Just return func.
        return func;
    };
    ```

5. In appCode.js testare i risultati digitando lo stesso codice digitato in precedenza. Questa volta, IntelliSense fornisce le informazioni desiderate.

     ![Esempio di override dei risultati di IntelliSense](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")

## <a name="see-also"></a>Vedere anche
 Completamento istruzioni [JavaScript IntelliSense](../ide/javascript-intellisense.md) [per gli identificatori](../ide/statement-completion-for-identifiers.md)
