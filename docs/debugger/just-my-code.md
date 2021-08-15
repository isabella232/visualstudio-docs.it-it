---
title: Eseguire il debug del codice utente con Just My Code | Microsoft Docs
description: Just My Code è una funzionalità di debug che esegue automaticamente il debug delle chiamate a codice non utente. Informazioni su come abilitare, disabilitare e usare questa funzionalità.
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
ms.topic: how-to
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2cdf4e14f61e051b282336fbeec2a53fffb89c8ff3316de1242b5f2c7ff8921f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121325094"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Eseguire il debug solo del codice utente con Just My Code

*Just My Code* è una funzionalità Visual Studio di debug che esegue automaticamente il debug delle chiamate a sistema, framework e altro codice non utente. Nella finestra **Stack di** chiamate Just My Code le chiamate vengono compresse in **frame [Codice esterno].**

Just My Code funziona in modo diverso nei progetti .NET, C++ e JavaScript.

## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Abilitare o disabilitare Just My Code

Per la maggior parte dei linguaggi di programmazione, Just My Code è abilitato per impostazione predefinita.

- Per abilitare o disabilitare Just My Code in Visual Studio, in Opzioni strumenti (o Opzioni di debug  >   )   >  > **Debug**  >  **generale** selezionare o deselezionare Abilita Just My Code .

![Abilitare Just My Code nella finestra di dialogo Opzioni](../debugger/media/dbg_justmycode_options.png "Abilita Just My Code")

> [!NOTE]
> **Abilita Just My Code** è un'impostazione globale che si applica a tutti i Visual Studio in tutti i linguaggi.

## <a name="just-my-code-debugging"></a>debug Just My Code

Durante una sessione  di debug, la finestra Moduli mostra i moduli di codice che il debugger sta trattando come My Code (codice utente), insieme al relativo stato di caricamento dei simboli. Per altre informazioni, vedere Acquisire familiarità con il modo [in cui il debugger si collega all'app.](../debugger/debugger-tips-and-tricks.md#modules_window)

![Codice utente nella finestra Moduli](../debugger/media/dbg_justmycode_module.png "Codice utente nella finestra Moduli")

Nella finestra Stack  **di** chiamate o Attività Just My Code comprime il codice non utente in una cornice di codice con annotazioni disattivata con etichetta `[External Code]` .

![Frame di codice esterno nella finestra Stack di chiamate](../debugger/media/dbg_justmycode_externalcode.png "Frame del codice esterno")

>[!TIP]
>Per aprire **moduli,** **stack di chiamate,** **attività** o la maggior parte delle altre finestre di debug, è necessario essere in una sessione di debug. Durante il debug,  >  **in Debug Windows** selezionare le finestre da aprire.

<a name="BKMK_Override_call_stack_filtering"></a>Per visualizzare il codice in un frame **[Codice esterno]** compresso, fare clic  con il pulsante destro del mouse nella finestra Stack di chiamate o Attività e scegliere Mostra codice esterno dal menu di scelta rapida.   Le righe di codice esterno espanse sostituiscono il frame **[External Code].**

![Mostra codice esterno nella finestra Stack di chiamate](../debugger/media/dbg_justmycode_showexternalcode.png "Mostra codice esterno")

> [!NOTE]
> **Mostra codice esterno** è un'impostazione corrente del profiler utente che si applica a tutti i progetti in tutti i linguaggi aperti dall'utente.

Facendo doppio clic su una riga di codice esterno espansa nella finestra **Stack** di chiamate la riga del codice chiamante viene evidenziata in verde nel codice sorgente. Per le DLL o altri moduli non trovati o caricati, potrebbe essere aperta una pagina simbolo o origine non trovata.

## <a name="net-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>.NET Just My Code

Nei progetti .NET vengono Just My Code file di simboli (con estensione *pdb)* e ottimizzazioni del programma per classificare il codice utente e non utente. Il debugger .NET considera i file binari ottimizzati e i file *PDB* non caricati come codice non utente.

Tre attributi del compilatore influiscono anche su ciò che il debugger .NET considera come codice utente:

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> indica al debugger che il codice a cui viene applicato non è codice utente.
- <xref:System.Diagnostics.DebuggerHiddenAttribute> nasconde il codice al debugger, anche se Just My Code è disattivato.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> indica al debugger di eseguire il codice a cui è applicato, anziché eseguire un'istruzione nel codice.

Il debugger .NET considera tutto il codice come codice utente.

Durante il debug di .NET:

- **Eseguire il debug**  >  **Eseguire un'istruzione** **(o F11)** per eseguire i passaggi del codice non utente sul codice alla riga di codice utente successiva.
- **Eseguire il debug**  >  **L'istruzione/uscita** **(o** + **MAIUSC F11)** nel codice non utente viene eseguita alla riga successiva del codice utente.

Se il codice utente non è più presente, il debug continua fino al termine, raggiunge un altro punto di interruzione o genera un errore.

<a name="BKMK_NET_Breakpoint_behavior"></a>Se il debugger si interrompe nel codice non utente(ad esempio, si usa **Debug**  >  **Interrompi** tutto e si sospende nel codice non utente), viene visualizzata la **finestra** Nessuna origine. È quindi possibile usare un **comando**  >  **Passaggio di** debug per passare alla riga di codice utente successiva.

Se si verifica un'eccezione non gestita nel codice non utente, il debugger si interrompe in corrispondenza della riga del codice utente in cui è stata generata l'eccezione.

Se per l'eccezione sono abilitate eccezioni first chance, la riga del codice utente chiamante viene evidenziata in verde nel codice sorgente. Nella **finestra Stack di** chiamate viene visualizzato il frame con annotazioni con etichetta **[Codice esterno]**.

## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> Just My Code in C++

A partire da Visual Studio 2017 versione 15.8, è supportata anche la Just My Code per l'esecuzione di istruzioni del codice. Questa funzionalità richiede anche l'uso dell'opzione del compilatore [/JMC (Just my code debugging).](/cpp/build/reference/jmc) L'opzione è abilitata per impostazione predefinita nei progetti C++. Per **il supporto della finestra** Stack di chiamate e dello stack di chiamate Just My Code, l'opzione /JMC non è necessaria.

<a name="BKMK_CPP_User_and_non_user_code"></a> Per essere classificato come codice utente, il file PDB per il file binario contenente il codice utente deve essere caricato dal debugger (usare la finestra **Moduli** per verificare questa operazione).

Per il comportamento dello stack di chiamate, ad esempio nella finestra **Stack** di chiamate, Just My Code in C++ considera solo queste funzioni *come codice non utente:*

- Funzioni con informazioni di origine rimosse nei propri file di simboli.
- Funzioni i cui file di simboli indicano che non esiste alcun file di origine corrispondente allo stack frame.
- Funzioni specificate nei *\* file natjmc* nella cartella *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers.*

Per il comportamento di esecuzione di istruzioni del codice, Just My Code in C++ considera solo queste funzioni *come codice non utente:*

- Funzioni per le quali il file PDB corrispondente non è stato caricato nel debugger.
- Funzioni specificate nei *\* file natjmc* nella cartella *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers.*

> [!NOTE]
> Per il supporto dell'esecuzione di istruzioni del codice in Just My Code, il codice C++ deve essere compilato usando i compilatori MSVC in Visual Studio 15.8 Preview 3 o versioni successive e l'opzione del compilatore /JMC deve essere abilitata (abilitata per impostazione predefinita). Per altri dettagli, vedere [Personalizzare lo stack di chiamate C++ e il](#BKMK_CPP_Customize_call_stack_behavior)comportamento di esecuzione delle istruzioni del codice ) e questo post di [blog.](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/) Per il codice compilato usando un compilatore precedente, i file *natstepfilter* sono l'unico modo per personalizzare l'esecuzione delle istruzioni del codice, che è indipendente dal Just My Code. Vedere [Personalizzare il comportamento di esecuzione di istruzioni C++.](#BKMK_CPP_Customize_stepping_behavior)

<a name="BKMK_CPP_Stepping_behavior"></a> Durante il debug di C++:

- **Eseguire il debug**  >  **Eseguire un'istruzione** **(o F11)** per eseguire i passaggi del codice non utente sul codice alla riga di codice utente successiva.
- **Eseguire il debug**  >  **L'istruzione/uscita** **(o** + **MAIUSC F11)** nel codice non utente viene eseguita alla riga successiva del codice utente.

Se il codice utente non è più presente, il debug continua fino al termine, raggiunge un altro punto di interruzione o genera un errore.

Se il debugger si interrompe nel codice non utente(ad esempio, si usa **Debug** Interrompi tutto e si sospende nel codice non utente), l'esecuzione di istruzioni continua nel codice  >   non utente.

Se il debugger rileva un'eccezione, si arresta in caso di eccezione, sia nel codice utente che in quello non utente. **Le opzioni non gestite dall'utente** nella **finestra di dialogo Impostazioni** eccezioni vengono ignorate.

### <a name="customize-c-call-stack-and-code-stepping-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a> Personalizzare lo stack di chiamate C++ e il comportamento di esecuzione di istruzioni del codice

Per i progetti C++, è possibile specificare i moduli, i file di origine e le funzioni che la finestra **Stack** di chiamate considera come codice non utente specificandoli nei file *\* natjmc.* Questa personalizzazione si applica anche all'esecuzione di istruzioni del codice se si usa il compilatore più recente (vedere [C++ Just My Code](#BKMK_CPP_User_and_non_user_code)).

- Per specificare il codice non utente per tutti gli utenti del computer che esegue Visual Studio, aggiungere il file con estensione *natjmc* alla cartella *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers*.
- Per specificare codice non utente per un singolo utente, aggiungere il file *natjmc* alla cartella *%USERPROFILE%\Documenti<Visual Studio versione \\ \> \Visualizers.*

Un file *natjmc* è un file XML con la sintassi seguente:

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
|`Name`|Obbligatorio. Percorso completo del modulo o dei moduli. È possibile usare il Windows caratteri jolly (zero o `?` un carattere) e `*` (zero o più caratteri). Ad esempio,<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> indica al debugger di considerare tutti i moduli nella cartella *\3rdParty\UtilLibs* di qualsiasi unità come codice esterno.|
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

### <a name="customize-c-stepping-behavior-independent-of-just-my-code-settings"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a> Personalizzare il comportamento di esecuzione delle istruzioni C++ indipendentemente Just My Code impostazioni

Nei progetti C++ è possibile specificare le funzioni di cui eseguire l'istruzione/esecuzione elencandole come codice non utente nei *\* file natstepfilter.* Le funzioni elencate *\* nei file natstepfilter* non dipendono dalle Just My Code predefinite.

- Per specificare codice non utente per tutti gli utenti Visual Studio locali, aggiungere il file *natstepfilter* alla cartella *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers.*
- Per specificare codice non utente per un singolo utente, aggiungere il file *natstepfilter* alla cartella *%USERPROFILE%\Documenti \\<Visual Studio versione \> \Visualizers.*

Un file *natstepfilter è* un file XML con la sintassi seguente:

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
|`Function`|Obbligatorio. Specifica una o più funzioni come funzioni non utente.|
|`Name`|Obbligatorio. Espressione regolare formattata in base a ECMA-262 che specifica il nome completo della funzione da mettere in corrispondenza. Esempio:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> indica al debugger che tutti i metodi in `MyNS::MyClass` devono essere considerati codice non utente. La corrispondenza prevede la distinzione tra maiuscole e minuscole.|
|`Module`|facoltativo. Espressione regolare formattata in base a ECMA-262 che specifica il percorso completo del modulo che contiene la funzione. La corrispondenza non fa distinzione tra maiuscole e minuscole.|
|`Action`|Obbligatorio. Uno dei valori seguenti (viene effettuata la distinzione tra maiuscole e minuscole):<br /><br /> `NoStepInto`  : indica al debugger di eseguire l'istruzione/istruzione della funzione.<br /> `StepInto`  : indica al debugger di eseguire un'istruzione alla funzione, eseguendo l'override di qualsiasi altro `NoStepInto` oggetto per la funzione corrispondente.|

## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> Just My Code in JavaScript

<a name="BKMK_JS_User_and_non_user_code"></a> JavaScript Just My Code l'esecuzione di istruzioni e la visualizzazione dello stack di chiamate categorizzando il codice in una di queste classificazioni:

|Classificazione|Descrizione|
|-|-|
|**MyCode**|Codice utente che si possiede e si controlla.|
|**LibraryCode**|Il codice non utente delle librerie usate regolarmente e l'app si basa su per funzionare correttamente, ad esempio WinJS o jQuery.|
|**UnrelatedCode**|Codice non utente nell'app di cui non si è proprietari e su cui l'app non si basa per funzionare correttamente. Ad esempio, un SDK pubblicitario che visualizza annunci potrebbe essere UnrelatedCode. Nei progetti UWP qualsiasi codice caricato nell'app da un URI HTTP o HTTPS viene considerato anche UnrelatedCode.|

Il debugger JavaScript classifica il codice come utente o non utente in questo ordine:

1. Classificazioni predefinite.
   - Lo script eseguito passando una stringa alla funzione fornita dall'host `eval` è **MyCode.**
   - Lo script eseguito passando una stringa al `Function` costruttore è **LibraryCode.**
   - Lo script in un riferimento al framework, ad esempio WinJS o Azure SDK, è **LibraryCode.**
   - Lo script eseguito passando una stringa alle `setTimeout` funzioni , o è `setImmediate` `setInterval` **UnrelatedCode.**

2. Classificazioni specificate per tutti Visual Studio progetti JavaScript nel file *%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.jsnel* file .

3. Le classificazioni nella *mycode.jsnel* file del progetto corrente.

Ogni passaggio di classificazione esegue l'override dei passaggi precedenti.

Tutto il resto del codice viene classificato come **MyCode**.

È possibile modificare le classificazioni predefinite e classificare URL e file specifici come codice utente o non utente, aggiungendo un *file* json denominato *mycode.jsnella* cartella radice di un progetto JavaScript. Vedere [Personalizzare javascript Just My Code](#BKMK_JS_Customize_Just_My_Code).

<a name="BKMK_JS_Stepping_behavior"></a> Durante il debug di JavaScript:

- Se una funzione è codice non utente, esegui il **debug** istruzione (o F11 ) si comporta come Esegui istruzione/istruzione di  >   **debug**   >   **(o F10).**
- Se un passaggio inizia nel codice non utente **(LibraryCode** o **UnrelatedCode),** l'esecuzione di istruzioni si comporta temporaneamente come se Just My Code non fosse abilitata. Quando si torna al codice utente, l'Just My Code viene ri abilitata.
- Quando un passaggio del codice utente comporta l'uscita dal contesto di esecuzione corrente, il debugger si arresta alla successiva riga di codice utente eseguita. Se ad esempio un callback viene eseguito nel codice **LibraryCode**, il debugger continua finché la riga di codice utente successiva non viene eseguita.
- **L'uscita** (o **MAIUSC** + **F11)** si interrompe alla riga di codice utente successiva.

Se il codice utente non è più presente, il debug continua fino al termine, raggiunge un altro punto di interruzione o genera un errore.

I punti di interruzione impostati nel codice vengono sempre raggiunto, ma il codice viene classificato.

- Se la `debugger` parola chiave si verifica in **LibraryCode**, il debugger si interrompe sempre.
- Se la `debugger` parola chiave si verifica in **UnrelatedCode**, il debugger non si arresta.

<a name="BKMK_JS_Exception_behavior"></a> Se si verifica un'eccezione non gestita nel **codice MyCode** o **LibraryCode,** il debugger si interrompe sempre.

Se si verifica un'eccezione non gestita in **UnrelatedCode** e **MyCode** o **LibraryCode** si trova nello stack di chiamate, il debugger si interrompe.

Se le eccezioni first-chance sono abilitate per l'eccezione e l'eccezione si verifica in **LibraryCode** o **UnrelatedCode:**

- Se l'eccezione è gestita, il debugger non si interrompe.
- Se l'eccezione non è gestita, il debugger si interrompe.

### <a name="customize-javascript-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a> Personalizzare le Just My Code JavaScript

Per classificare il codice utente e non utente per un singolo progetto JavaScript, è possibile aggiungere un file *con estensione* *json* denominatomycode.jsnella cartella radice del progetto.

Le specifiche in questo file sostituiscono le classificazioni predefinite e le *mycode.default.wwa.jsnel* file. Il *mycode.jsnel* file non deve elencare tutte le coppie chiave-valore. I **valori MyCode**, **Libraries** e **Unrelated** possono essere matrici vuote.

*Mycode.jsfile usano* questa sintassi:

```json
{
    "Eval" : "Classification",
    "Function" : "Classification",
    "ScriptBlock" : "Classification",
    "MyCode" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ],
    "Libraries" : [
        "UrlOrFileSpec",
        . .
        "UrlOrFileSpec"
    ],
    "Unrelated" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ]
}

```

**Eval, Function e ScriptBlock**

Le coppie chiave-valore **Eval**, **Function** e **ScriptBlock** determinano come viene classificato il codice generato dinamicamente:

|Nome|Descrizione|
|-|-|
|**Eval**|Script eseguito passando una stringa alla funzione `eval` fornita dall'host. Per impostazione predefinita, lo script Eval viene classificato come **MyCode**.|
|**Funzione**|Script eseguito passando una stringa al costruttore `Function`. Per impostazione predefinita, lo script Function viene classificato come **LibraryCode**.|
|**ScriptBlock**|Script eseguito passando una stringa alla funzione `setTimeout`, `setImmediate` o `setInterval`. Per impostazione predefinita, lo script ScriptBlock viene classificato come **UnrelatedCode**.|

È possibile modificare il valore a una delle parole chiave seguenti:

- `MyCode` classifica lo script come **MyCode**.
- `Library` classifica lo script come **LibraryCode**.
- `Unrelated` classifica lo script come **UnrelatedCode**.

**MyCode, Libraries e Unrelated**

Le coppie chiave-valore **MyCode**, **Libraries** e **Unrelated** specificano gli URL o i file da includere in una classificazione:

|Nome|Descrizione|
|-|-|
|**MyCode**|Matrice di URL o di file classificati come **MyCode**.|
|**Raccolte**|Matrice di URL o di file classificati come **LibraryCode**.|
|**Unrelated**|Matrice di URL o di file classificati come **UnrelatedCode**.|

L'URL o la stringa di file può contenere uno o più `*` caratteri, che corrispondono a zero o più caratteri. `*` è uguale all'espressione regolare `.*` .
