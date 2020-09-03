---
title: Just My Code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 62da3a36a34a2111bb139765268fbb0bef9b500d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531924"
---
# <a name="just-my-code"></a>Just My Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli sviluppatori che utilizzano i linguaggi .NET Framework hanno familiarità con la funzionalità di debug Just My Code che ignora chiamate di sistema e del framework e altre chiamate non di utenti e le comprime nelle finestre dello stack di chiamate. La funzionalità Just My Code è stata estesa ai linguaggi C++ e JavaScript. In questo argomento vengono descritte le specifiche di utilizzo di Just My Code in progetti .NET Framework, C++ nativo e JavaScript.  
  
## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Abilitare o disabilitare Just My Code  
 Per abilitare o disabilitare Just My Code, scegliere **Opzioni e impostazioni** dal menu **debug** . Nel nodo **Debugging**  /  **generale** debug scegliere o deselezionare **Abilita Just My Code**.  
  
 ![Abilitare Just My Code nella finestra di dialogo Opzioni](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> L'impostazione **abilita Just My Code** è un'impostazione globale applicata a tutti i progetti di Visual Studio in tutte le lingue.  
  
### <a name="override-call-stack-filtering"></a><a name="BKMK_Override_call_stack_filtering"></a> Esegui override filtro stack di chiamate  
 Nelle visualizzazioni dello stack di chiamate, ad esempio nelle finestre dello stack di chiamate e delle attività, la funzionalità Just My Code consente di comprimere il codice non utente in un frame annotato con etichetta `[External Code]`. Per visualizzare i frame compressi, scegliere **Mostra codice esterno** nel menu di scelta rapida della visualizzazione dello stack di chiamate.  
  
> [!NOTE]
> L'impostazione **Mostra codice esterno** viene salvata nel profiler dell'utente corrente. e si applica a tutti i progetti in tutti i linguaggi aperti dall'utente.  
  
## <a name="net-framework-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a> .NET Framework Just My Code  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_NET_User_and_non_user_code"></a> Codice utente e non utente  
 Per distinguere il codice utente dal codice non utente, Just My Code esamina i file di simboli (con estensione pdb) e le ottimizzazioni del programma. Il debugger considera il codice come codice non utente quando il file binario è ottimizzato o quando il file con estensione pdb non è disponibile.  
  
 Tre ulteriori attributi influiscono sul codice che viene considerato My Code dal debugger:  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> indica al debugger che il codice a cui è applicato non è My Code.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> nasconde il codice al debugger, anche se Just My Code è disattivato.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> indica al debugger di eseguire un'istruzione alla volta il codice a cui viene applicato, anziché eseguire tutto il codice.  
  
  Tutto il codice rimanente viene considerato codice utente.  
  
### <a name="stepping-behavior"></a><a name="BKMK_NET_Stepping_behavior"></a> Esecuzione del comportamento  
 Quando si esegue l'istruzione (scelta rapida da tastiera: F11) codice non utente, il debugger esegue il **passaggio** del codice alla successiva istruzione utente. Quando si **esce dall'istruzione/uscita** (tastiera: MAIUSC + F11), il debugger viene eseguito fino alla riga successiva del codice utente. Se non viene rilevato nessun codice utente l'esecuzione continua finché non viene chiusa l'applicazione, non viene trovato un punto di interruzione o non si verifica un'eccezione.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_NET_Breakpoint_behavior"></a> Comportamento punto di interruzione  
 Quando Just My Code è abilitato, è possibile scegliere **Interrompi tutto** (tastiera: CTRL + ALT + INTERR) e arrestare l'esecuzione in una posizione in cui non è presente codice utente da visualizzare. In questo caso viene visualizzata la finestra Nessuna origine. Se a questo punto si sceglie un comando di esecuzione, il debugger passerà alla successiva riga del codice utente.  
  
### <a name="exception-behavior"></a><a name="BKMK_NET_Exception_behavior"></a> Comportamento dell'eccezione  
 Se si verifica un'eccezione non gestita nel codice non utente, il debugger si interrompe alla riga del codice utente in cui l'eccezione è stata generata.  
  
 Se per l'eccezione sono abilitate le eccezioni first-chance, la riga di codice utente viene evidenziata in verde. Nello stack di chiamate viene visualizzato un frame con annotazioni **con etichetta [codice esterno]**.  
  
## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> Just My Code in C++  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_CPP_User_and_non_user_code"></a> Codice utente e non utente  
 Just My Code in C++ è diverso da Just My Code in .NET Framework e in JavaScript perché il comportamento dell'esecuzione di istruzioni è indipendente da quello dello stack di chiamate.  
  
 **Stack di chiamate**  
  
 Per impostazione predefinita, nelle finestre dello stack di chiamate il debugger considera le funzioni seguenti come codice non utente:  
  
- Funzioni con informazioni di origine rimosse nei propri file di simboli.  
  
- Funzioni i cui file di simboli indicano che non esiste alcun file di origine corrispondente allo stack frame.  
  
- Funzioni specificate nei file `*.natjmc` e nella cartella `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`.  
  
  **Esecuzione di istruzioni**  
  
  Per impostazione predefinita solo le funzioni specificate nei file `*.natstepfilter` nella cartella `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` vengono considerate codice non utente.  
  
  È possibile creare i propri file `.natstepfilter` e `.natjmc` per personalizzare il comportamento dell'esecuzione di istruzioni e della finestra dello stack di chiamate in `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`.  
  
### <a name="stepping-behavior"></a><a name="BKMK_CPP_Stepping_behavior"></a> Esecuzione del comportamento  
 Quando si esegue l'istruzione (scelta rapida da tastiera: F11) del codice non utente dal codice utente, il debugger esegue il **passaggio** del codice alla riga successiva del codice utente. Quando si **esce dall'istruzione/uscita** (tastiera: MAIUSC + F11), il debugger viene eseguito fino alla riga successiva del codice utente. Se non viene rilevato nessun codice utente l'esecuzione continua finché non viene chiusa l'applicazione, non viene trovato un punto di interruzione o non si verifica un'eccezione.  
  
 Se il debugger si interrompe nel codice non utente, ad esempio se un comando Interrompi tutto si arresta nel codice non utente, l'esecuzione continua nel codice non utente.  
  
### <a name="exception-behavior"></a><a name="BKMK_CPP_Exception_behavior"></a> Comportamento dell'eccezione  
 Quando il debugger raggiunge un'eccezione, verrà arrestato sull'eccezione indipendentemente che il codice sia utente o non utente. Le opzioni non **gestite dall'utente** nella finestra di dialogo **eccezioni** vengono ignorate.  
  
### <a name="customize-stepping-behavior"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a> Personalizzare il comportamento dell'esecuzione  
 È possibile specificare le funzioni da ignorare elencandole come codice non utente nei file `*.natstepfilter`.  
  
- Per specificare il codice non utente per tutti gli utenti del computer di Visual Studio, aggiungere il file con estensione natstepfilter alla `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` cartella.  
  
- Per specificare il codice non utente per un singolo utente, aggiungere il file con estensione natstepfilter alla `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` cartella.  
  
  I file con estensione natstepfilter sono file XML con la sintassi seguente:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Action>StepAction</Action>  
    </Function>  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Module>ModuleSpec</Module>  
        <Action>StepAction</Action>  
    </Function>  
</StepFilter>  
  
```  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Funzione|Obbligatorio. Specifica una o più funzioni come funzioni non utente.|  
|`Name`|Obbligatorio. Espressione regolare formattata in base a ECMA-262 che specifica il nome completo della funzione da mettere in corrispondenza. Ad esempio:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> indica al debugger che tutti i metodi in `MyNS::MyClass` devono essere considerati codice non utente. La corrispondenza prevede la distinzione tra maiuscole e minuscole.|  
|`Module`|facoltativo. Espressione regolare formattata in base a ECMA-262 che specifica il percorso completo del modulo che contiene la funzione. La corrispondenza non fa distinzione tra maiuscole e minuscole.|  
|`Action`|Obbligatorio. Uno dei valori seguenti (viene effettuata la distinzione tra maiuscole e minuscole):<br /><br /> -   `NoStepInto`  : indica al debugger di eseguire un'istruzione/routine della funzione corrispondente.<br />-   `StepInto`  : indica al debugger di eseguire un'istruzione nelle funzioni corrispondenti, eseguendo l'override di qualsiasi altro oggetto `NoStepInto` per le funzioni corrispondenti.|  
  
### <a name="customize-call-stack-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a> Personalizzare il comportamento dello stack di chiamate  
 È possibile specificare i moduli, i file di origine e le funzioni da trattare come codice non utente negli stack di chiamate specificandoli nei file `*.natjmc`.  
  
- Per specificare il codice non utente per tutti gli utenti del computer di Visual Studio, aggiungere il file con estensione natjmc alla `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` cartella.  
  
- Per specificare il codice non utente per un singolo utente, aggiungere il file con estensione natjmc alla `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` cartella.  
  
  I file con estensione natjmc sono file XML con la sintassi seguente:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">  
  
  <!-- Modules -->  
  <Module Name="ModuleSpec" />  
  <Module Name="ModuleSpec" Company="CompanyName" />  
  
  <!-- Files -->  
  <File Name="FileSpec"/>  
  
  <!-- Functions -->  
  <Function Name="FunctionSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />  
  
</NonUserCode>  
  
```  
  
 **Attributi dell'elemento modulo**  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio. Percorso completo del modulo o dei moduli. È possibile usare i caratteri jolly di Windows `?` (zero o un carattere) e `*` (zero o più caratteri). Ad esempio:<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> indica al debugger di considerare tutti i moduli nella cartella in `\3rdParty\UtilLibs` di qualsiasi unità come codice esterno.|  
|`Company`|facoltativo. Nome della società che pubblica il modulo che viene incorporato nel file eseguibile. È possibile utilizzare questo attributo per evitare ambiguità tra i moduli.|  
  
 **Attributi dell'elemento file**  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio. Percorso completo del file o dei file di codice sorgente da considerare come codice esterno. È possibile usare i caratteri jolly di Windows `?` e `*` quando si specifica il percorso.|  
  
 **Attributi dell'elemento funzione**  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio. Nome completo della funzione da considerare come codice esterno.|  
|`Module`|facoltativo. Nome o percorso completo del modulo che contiene la funzione. È possibile utilizzare questo attributo per evitare ambiguità tra funzioni con lo stesso nome.|  
|`ExceptionImplementation`|Se impostato su `true`, lo stack di chiamate mostra la funzione che ha generato l'eccezione anziché questa funzione.|  
  
## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> Just My Code in JavaScript  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_JS_User_and_non_user_code"></a> Codice utente e non utente  
 **Classificazioni del codice**  
  
 Just My Code in JavaScript controlla l'esecuzione e la visualizzazione dello stack di chiamate suddividendo il codice in una delle classificazioni seguenti:  
  
|Name|Descrizione|
|-|-|  
|**MyCode**|Codice utente che si possiede e si controlla.|  
|**LibraryCode**|Codice non utente da librerie utilizzate regolarmente e su cui si basa l'applicazione per essere eseguita correttamente (ad esempio WinJS o jQuery).|  
|**UnrelatedCode**|Codice non utente che potrebbe essere in esecuzione nell'applicazione, ma di cui non si è proprietari e che l'applicazione non si basa direttamente su di essa per funzionare correttamente, ad esempio un SDK pubblicitario che Visualizza annunci. Nei progetti Windows Store tutto il codice caricato nell'applicazione da un URI HTTP o HTTPS viene anche considerato UnrelatedCode.|  
  
 Il debugger JavaScript classifica automaticamente questi tipi di codice:  
  
- Lo script che viene eseguito passando una stringa alla funzione fornita dall'host `eval` viene classificato come **codice**.  
  
- Uno script eseguito passando una stringa al `Function` costruttore viene classificato come **LibraryCode**.  
  
- Uno script contenuto in un riferimento a un Framework, ad esempio WinJS o Azure SDK, viene classificato come **LibraryCode**.  
  
- Lo script che viene eseguito passando una stringa alle `setTimeout` funzioni, `setImmediate` o `setInterval` viene classificato come **UnrelatedCode**.  
  
- `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` specifica altro codice non utente e utente per tutti i progetti di Visual Studio JavaScript.  
  
  È possibile modificare le classificazioni predefinite e classificare file e URL specifici aggiungendo un file con estensione json denominato `mycode.json` nella cartella radice di un progetto.  
  
  Tutto il resto del codice viene classificato come **MyCode**.  
  
### <a name="stepping-behavior"></a><a name="BKMK_JS_Stepping_behavior"></a> Esecuzione del comportamento  
  
- Se una funzione non è codice utente (**Decode**), **Esegui istruzione** (tasto di scelta rapida: F11) si comporta come **Esegui istruzione** /routine (tastiera: F10).  
  
- Se un passaggio inizia con un codice non utente (**LibraryCode** o **UnrelatedCode**), l'esecuzione temporanea di si comporta come se Just My Code non fosse abilitata. Non appena si esegue nuovamente codice utente, l'esecuzione di Just My Code è nuovamente abilitata.  
  
- Quando un'esecuzione nel codice utente comporta l'uscita dal contesto di esecuzione corrente (ad esempio eseguire l'ultima riga di un gestore eventi), il debugger si arresta alla successiva riga di codice utente eseguita. Se, ad esempio, un callback viene eseguito nel codice **LibraryCode** , il debugger continua fino a quando non viene eseguita la riga successiva del codice utente.  
  
- **Esci da istruzione/uscita** (tastiera: MAIUSC + F11) si interrompe alla riga successiva del codice utente. Se non viene rilevato nessun codice utente l'esecuzione continua finché non viene chiusa l'applicazione, non viene trovato un punto di interruzione o non si verifica un'eccezione.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_JS_Breakpoint_behavior"></a> Comportamento punto di interruzione  
  
- I punti di interruzione impostati nel codice verranno raggiunti sempre indipendentemente dalla classificazione del codice.  
  
- Se la parola chiave `debugger` viene rilevata in:  
  
  - Il codice **LibraryCode** , il debugger si interrompe sempre.  

  - Codice **UnrelatedCode** , il debugger non si arresta.  
  
### <a name="exception-behavior"></a><a name="BKMK_JS_Exception_behavior"></a> Comportamento dell'eccezione  
 Se un'eccezione non gestita viene generata in:  
  
- **Codice** **LibraryCode** , il debugger si interrompe sempre.  
  
- Il codice **UnrelatedCode** e **il codice** **LibraryCode o** si trova nello stack di chiamate, il debugger viene interrotto.  
  
  Se le eccezioni first-chance sono abilitate per l'eccezione nella finestra di dialogo eccezioni e l'eccezione viene generata nel codice **LibraryCode** o **UnrelatedCode** :  
  
- Se l'eccezione è gestita, il debugger non si interrompe.  
  
- Se l'eccezione non è gestita, il debugger si interrompe.  
  
### <a name="customize-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a> Personalizzare Just My Code  
 Per classificare il codice utente e non utente per un singolo progetto di Visual Studio, aggiungere un file con estensione json denominato `mycode.json` nella cartella radice del progetto.  
  
 Le classificazioni vengono eseguite nell'ordine seguente:  
  
1. Classificazioni predefinite  
  
2. Classificazioni nel file `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json`  
  
3. Classificazioni nel file `mycode. json` del progetto corrente.  
  
   Ogni passaggio di classificazione esegue l'override dei passaggi precedenti. Un file con estensione JSON non deve elencare tutte le coppie chiave-valore e il **codice**, le **librerie**e i valori non **correlati** possono essere matrici vuote.  
  
   I file My Code con estensione json utilizzano la sintassi seguente:  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec”,  
        . .  
        "UrlOrFileSpec”  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ]  
}  
  
```  
  
 **Eval, Function e ScriptBlock**  
  
 Le coppie chiave-valore **EVAL**, **Function**e **scriptblock** determinano il modo in cui viene classificato il codice generato dinamicamente.  
  
|Name|Descrizione|
|-|-|  
|**Eval**|Script eseguito passando una stringa alla funzione `eval` fornita dall'host. Per impostazione predefinita, lo script Eval viene classificato come **MyCode**.|  
|**Funzione**|Script eseguito passando una stringa al costruttore `Function`. Per impostazione predefinita, lo script Function viene classificato come **LibraryCode**.|  
|**ScriptBlock**|Script eseguito passando una stringa alla funzione `setTimeout`, `setImmediate` o `setInterval`. Per impostazione predefinita, lo script ScriptBlock viene classificato come **UnrelatedCode**.|  
  
 È possibile modificare il valore a una delle parole chiave seguenti:  
  
- `MyCode`  classifica lo script come **codice**.  
  
- `Library`  classifica lo script come **LibraryCode**.  
  
- `Unrelated`  classifica lo script come **UnrelatedCode**.  
  
  **MyCode, Libraries e Unrelated**  
  
  Le coppie **codice**, **librerie**e valore chiave non **correlate** specificano gli URL o i file che si desidera includere in una classificazione:  
  
|Name|Descrizione|
|-|-|  
|**MyCode**|Matrice di URL o file classificati come **codice**.|  
|**Raccolte**|Matrice di URL o di file classificati come **LibraryCode**.|  
|**Unrelated**|Matrice di URL o di file classificati come **UnrelatedCode**.|  
  
 La stringa dell'URL o del file può contenere uno o più caratteri `*`, che corrispondono a zero o più caratteri. `*` è l'equivalente dell'espressione regolare `.*`.
