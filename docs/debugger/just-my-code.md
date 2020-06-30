---
title: Eseguire il debug del codice utente con Just My Code | Microsoft Docs
ms.date: 02/13/2019
ms.topic: how-to
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 867477fd3e490f91e81fb91c8be267ede83c8d2c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536565"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Esegui il debug solo del codice utente con Just My Code

*Just My Code* è una funzionalità di debug di Visual Studio che esegue automaticamente le chiamate a sistemi, Framework e altro codice non utente. Nella finestra **stack di chiamate** Just My Code comprime tali chiamate in frame **[codice esterno]** .

Just My Code funziona in modo diverso nei progetti .NET, C++ e JavaScript.

## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Abilitare o disabilitare Just My Code

Per la maggior parte dei linguaggi di programmazione, Just My Code è abilitato per impostazione predefinita.

- Per abilitare o disabilitare Just My Code in Visual Studio, in **strumenti**  >  **Opzioni** (o **Debug**  >  **Opzioni**di debug) > **debug**  >  **generale**selezionare o deselezionare **Abilita Just My Code**.

![Abilitare Just My Code nella finestra di dialogo Opzioni](../debugger/media/dbg_justmycode_options.png "Abilita Just My Code")

> [!NOTE]
> **Enable Just My Code** è un'impostazione globale che si applica a tutti i progetti di Visual Studio in tutte le lingue.

## <a name="just-my-code-debugging"></a>debug Just My Code

Durante una sessione di debug, nella finestra **moduli** vengono visualizzati i moduli di codice che il debugger sta trattando come codice utente (codice utente), insieme al relativo stato di caricamento dei simboli. Per altre informazioni, vedere [acquisire familiarità con la modalità di connessione del debugger all'app](../debugger/debugger-tips-and-tricks.md#modules_window).

![Codice utente nella finestra moduli](../debugger/media/dbg_justmycode_module.png "Codice utente nella finestra moduli")

Nella finestra **stack di chiamate** o **attività** Just My Code comprime il codice non utente in un frame di codice con annotazioni grigio con etichetta `[External Code]` .

![Frame di codice esterno nella finestra stack di chiamate](../debugger/media/dbg_justmycode_externalcode.png "Cornice codice esterno")

>[!TIP]
>Per aprire i **moduli**, lo **stack di chiamate**, le **attività**o la maggior parte delle altre finestre di debug, è necessario essere in una sessione di debug. Durante il debug, in finestre di **debug**  >  **Windows**selezionare le finestre che si desidera aprire.

<a name="BKMK_Override_call_stack_filtering"></a>Per visualizzare il codice in un frame compresso **[codice esterno]** , fare clic con il pulsante destro del mouse nella finestra **stack di chiamate** o **attività** e scegliere **Mostra codice esterno** dal menu di scelta rapida. Le righe di codice esterno espanse sostituiscono il frame **[codice esterno**].

![Mostra codice esterno nella finestra stack di chiamate](../debugger/media/dbg_justmycode_showexternalcode.png "Mostra codice esterno")

> [!NOTE]
> **Mostra codice esterno** è un'impostazione del profiler utente corrente che si applica a tutti i progetti in tutte le lingue aperte dall'utente.

Facendo doppio clic su una riga di codice esterna espansa nella finestra **stack di chiamate** viene evidenziata la riga del codice chiamante in verde nel codice sorgente. Per le dll o altri moduli non trovati o caricati, è possibile che venga visualizzata una pagina di simboli o di origine non trovata.

## <a name="net-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>Just My Code .NET

Nei progetti .NET Just My Code utilizza i file di simboli (con*estensione PDB*) e le ottimizzazioni del programma per classificare il codice utente e non utente. Il debugger .NET considera i file binari ottimizzati e i file con *estensione PDB* non caricati come codice non utente.

Tre attributi del compilatore influiscono anche sul codice utente considerato dal debugger .NET:

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute>indica al debugger che il codice a cui è applicato non è il codice utente.
- <xref:System.Diagnostics.DebuggerHiddenAttribute> nasconde il codice al debugger, anche se Just My Code è disattivato.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute>indica al debugger di esaminare il codice a cui è applicato, anziché eseguire un'istruzione nel codice.

Il debugger .NET considera il codice utente in tutto il codice.

Durante il debug di .NET:

- **Esegui debug**  >  Eseguire un' **istruzione** (o **F11**) sui passaggi del codice non utente sul codice alla riga successiva del codice utente.
- **Esegui debug**  >  **Esci da istruzione/uscita** (o **MAIUSC** + **F11**) nel codice non utente viene eseguito alla riga successiva del codice utente.

Se non c'è altro codice utente, il debug continua fino a quando non termina, raggiunge un altro punto di interruzione o genera un errore.

<a name="BKMK_NET_Breakpoint_behavior"></a>Se il debugger si interrompe nel codice non utente, ad esempio se si usa il **debug**  >  **Interrompi tutto** e si sospende nel codice non utente, viene visualizzata la finestra **Nessuna origine** . È quindi possibile usare un comando **debug**  >  **Step** per passare alla riga successiva del codice utente.

Se si verifica un'eccezione non gestita nel codice non utente, il debugger si interrompe in corrispondenza della riga del codice utente in cui è stata generata l'eccezione.

Se per l'eccezione sono abilitate le eccezioni first-chance, la riga del codice utente chiamante viene evidenziata in verde nel codice sorgente. Nella finestra **stack di chiamate** viene visualizzato il frame con annotazioni con etichetta **[codice esterno]**.

## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> Just My Code in C++

A partire da Visual Studio 2017 versione 15,8, è supportato anche Just My Code per l'esecuzione del codice. Questa funzionalità richiede anche l'uso dell'opzione del compilatore [/JMC (Just My Code debug)](/cpp/build/reference/jmc) . Per impostazione predefinita, l'opzione è abilitata nei progetti C++. Per la finestra **stack di chiamate** e il supporto dello stack di chiamate in Just My Code, l'opzione/JMC non è obbligatoria.

<a name="BKMK_CPP_User_and_non_user_code"></a>Per essere classificato come codice utente, il PDB per il file binario che contiene il codice utente deve essere caricato dal debugger (usare la finestra **moduli** per verificare questa impostazione).

Per il comportamento dello stack di chiamate, ad esempio nella finestra **stack di chiamate** , Just My Code in C++ considera solo queste funzioni come *codice non utente*:

- Funzioni con informazioni di origine rimosse nei propri file di simboli.
- Funzioni i cui file di simboli indicano che non esiste alcun file di origine corrispondente allo stack frame.
- Funzioni specificate nei file con * \* estensione natjmc* nella cartella *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* .

Per il comportamento dell'esecuzione del codice, Just My Code in C++ considera solo queste funzioni come *codice non utente*:

- Funzioni per le quali il file PDB corrispondente non è stato caricato nel debugger.
- Funzioni specificate nei file con * \* estensione natjmc* nella cartella *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* .

> [!NOTE]
> Per il supporto dell'esecuzione del codice in Just My Code, è necessario compilare il codice C++ usando i compilatori MSVC in Visual Studio 15,8 Preview 3 o versioni successive e l'opzione del compilatore/JMC deve essere abilitata (è abilitata per impostazione predefinita). Per altri dettagli, vedere [personalizzare lo stack di chiamate C++ e il comportamento dell'esecuzione del codice](#BKMK_CPP_Customize_call_stack_behavior)) e questo [post di Blog](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/). Per il codice compilato usando un compilatore precedente, i file con *estensione natstepfilter* sono l'unico modo per personalizzare l'esecuzione del codice, che è indipendente da Just My Code. Vedere [personalizzare il comportamento dell'esecuzione di un linguaggio C++](#BKMK_CPP_Customize_stepping_behavior).

<a name="BKMK_CPP_Stepping_behavior"></a>Durante il debug di C++:

- **Esegui debug**  >  Eseguire un' **istruzione** (o **F11**) sui passaggi del codice non utente sul codice alla riga successiva del codice utente.
- **Esegui debug**  >  **Esci da istruzione/uscita** (o **MAIUSC** + **F11**) nel codice non utente viene eseguito alla riga successiva del codice utente.

Se non c'è altro codice utente, il debug continua fino a quando non termina, raggiunge un altro punto di interruzione o genera un errore.

Se il debugger si interrompe nel codice non utente, ad esempio se si usa il **debug**  >  **Interrompi tutto** e Sospendi nel codice non utente, l'esecuzione continua nel codice non utente.

Se il debugger rileva un'eccezione, si interrompe sull'eccezione, che si trovi nel codice utente o non utente. Le opzioni non **gestite dall'utente** nella finestra di dialogo **Impostazioni eccezioni** vengono ignorate.

### <a name="customize-c-call-stack-and-code-stepping-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a>Personalizzare lo stack di chiamate C++ e il comportamento dell'esecuzione del codice

Per i progetti C++, è possibile specificare i moduli, i file di origine e le funzioni che la finestra **stack di chiamate** considera come codice non utente specificando tali moduli nei file * \* . natjmc* . Questa personalizzazione si applica anche all'esecuzione del codice se si usa il compilatore più recente (vedere [C++ Just My Code](#BKMK_CPP_User_and_non_user_code)).

- Per specificare il codice non utente per tutti gli utenti del computer che esegue Visual Studio, aggiungere il file con estensione *natjmc* alla cartella *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers*.
- Per specificare il codice non utente per un singolo utente, aggiungere il file con *estensione natjmc* ai *documenti%userprofile%\My \\<cartella di Visual Studio versione \> \Visualizers* .

Un file con *estensione natjmc* è un file XML con la sintassi seguente:

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
|`Name`|Obbligatorio. Percorso completo del modulo o dei moduli. È possibile usare i caratteri jolly `?` di Windows (zero o un carattere) e `*` (zero o più caratteri). Ad esempio,<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> indica al debugger di considerare tutti i moduli nella cartella *\3rdParty\UtilLibs* di qualsiasi unità come codice esterno.|
|`Company`|Facoltativa. Nome della società che pubblica il modulo che viene incorporato nel file eseguibile. È possibile utilizzare questo attributo per evitare ambiguità tra i moduli.|

 **Attributi dell'elemento file**

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Obbligatorio. Percorso completo del file o dei file di codice sorgente da considerare come codice esterno. È possibile usare i caratteri jolly di Windows `?` e `*` quando si specifica il percorso.|

 **Attributi dell'elemento funzione**

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Obbligatorio. Nome completo della funzione da considerare come codice esterno.|
|`Module`|Facoltativa. Nome o percorso completo del modulo che contiene la funzione. È possibile utilizzare questo attributo per evitare ambiguità tra funzioni con lo stesso nome.|
|`ExceptionImplementation`|Se impostato su `true`, lo stack di chiamate mostra la funzione che ha generato l'eccezione anziché questa funzione.|

### <a name="customize-c-stepping-behavior-independent-of-just-my-code-settings"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a>Personalizzare il comportamento dell'esecuzione di un linguaggio C++ indipendentemente dalle impostazioni Just My Code

Nei progetti C++ è possibile specificare le funzioni per eseguire un'istruzione/routine elencando tali funzioni come codice non utente nei file con * \* estensione natstepfilter* . Le funzioni elencate nei file con * \* estensione natstepfilter* non dipendono dalle impostazioni di Just My Code.

- Per specificare il codice non utente per tutti gli utenti locali di Visual Studio, aggiungere il file con *estensione natstepfilter* alla cartella *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* .
- Per specificare il codice non utente per un singolo utente, aggiungere il file con *estensione natstepfilter* ai *documenti%userprofile%\My \\<cartella di Visual Studio versione \> \Visualizers* .

Un file con *estensione natstepfilter* è un file XML con la sintassi seguente:

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
|`Name`|Obbligatorio. Espressione regolare formattata in base a ECMA-262 che specifica il nome completo della funzione da mettere in corrispondenza. Ad esempio:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> indica al debugger che tutti i metodi in `MyNS::MyClass` devono essere considerati codice non utente. La corrispondenza prevede la distinzione tra maiuscole e minuscole.|
|`Module`|Facoltativa. Espressione regolare formattata in base a ECMA-262 che specifica il percorso completo del modulo che contiene la funzione. La corrispondenza non fa distinzione tra maiuscole e minuscole.|
|`Action`|Obbligatorio. Uno dei valori seguenti (viene effettuata la distinzione tra maiuscole e minuscole):<br /><br /> `NoStepInto`: indica al debugger di eseguire un'istruzione/routine della funzione.<br /> `StepInto`: indica al debugger di eseguire un'istruzione nella funzione, eseguendo l'override di qualsiasi altro oggetto `NoStepInto` per la funzione corrispondente.|

## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> Just My Code in JavaScript

<a name="BKMK_JS_User_and_non_user_code"></a>JavaScript Just My Code controlla lo stato di avanzamento e visualizzazione dello stack di chiamate categorizzando il codice in una delle classificazioni seguenti:

|Classificazione|Descrizione|
|-|-|
|**MyCode**|Codice utente che si possiede e si controlla.|
|**LibraryCode**|Codice non utente dalle librerie usate regolarmente e l'app si basa su per funzionare correttamente (ad esempio, WinJS o jQuery).|
|**UnrelatedCode**|Codice non utente nell'app di cui non si è proprietari e che l'app non si basa sul funzionamento corretto. Ad esempio, un SDK pubblicitario che Visualizza annunci potrebbe essere UnrelatedCode. Nei progetti UWP, anche il codice caricato nell'app da un URI HTTP o HTTPS viene considerato UnrelatedCode.|

Il debugger JavaScript classifica il codice come utente o non utente nell'ordine seguente:

1. Classificazioni predefinite.
   - Lo script eseguito passando una stringa alla funzione fornita dall'host `eval` è **Decode**.
   - Lo script eseguito passando una stringa al `Function` costruttore è **LibraryCode**.
   - Lo script in un riferimento di Framework, ad esempio WinJS o Azure SDK, è **LibraryCode**.
   - Lo script eseguito passando una stringa alle `setTimeout` funzioni, `setImmediate` o `setInterval` è **UnrelatedCode**.

2. Classificazioni specificate per tutti i progetti JavaScript di Visual Studio in *% VSInstallDirectory% \JavaScript\JustMyCode\mycode.default.wwa.jssu* file.

3. Classificazioni nel *mycode.js* file del progetto corrente.

Ogni passaggio di classificazione esegue l'override dei passaggi precedenti.

Tutto il resto del codice viene classificato come **MyCode**.

È possibile modificare le classificazioni predefinite e classificare URL e file specifici come codice utente o non utente, aggiungendo un file con *estensione JSON* denominato *mycode.js* alla cartella radice di un progetto JavaScript. Vedere [personalizzare Just My Code JavaScript](#BKMK_JS_Customize_Just_My_Code).

<a name="BKMK_JS_Stepping_behavior"></a>Durante il debug di JavaScript:

- Se una funzione è un codice non utente, **Debug**  >  il debug di un'**istruzione** (o **F11**) si comporta come un **Debug**  >  **passaggio** di debug (o **F10**).
- Se un passaggio inizia con il codice non utente (**LibraryCode** o **UnrelatedCode**), l'esecuzione temporanea si comporta come se Just My Code non fosse abilitata. Quando si torna al codice utente, Just My Code esecuzione di istruzioni viene riabilitata.
- Quando un passaggio del codice utente determina l'uscita dal contesto di esecuzione corrente, il debugger si arresta alla successiva riga del codice utente eseguito. Se ad esempio un callback viene eseguito nel codice **LibraryCode**, il debugger continua finché la riga di codice utente successiva non viene eseguita.
- **Esci da istruzione/uscita** (o **MAIUSC** + **F11**) nella riga successiva del codice utente.

Se non c'è altro codice utente, il debug continua fino a quando non termina, raggiunge un altro punto di interruzione o genera un errore.

I punti di interruzione impostati nel codice vengono sempre raggiunti, ma il codice è classificato.

- Se la `debugger` parola chiave viene eseguita in **LibraryCode**, il debugger interrompe sempre l'esecuzione.
- Se la `debugger` parola chiave viene eseguita in **UnrelatedCode**, il debugger non si arresta.

<a name="BKMK_JS_Exception_behavior"></a>Se si verifica un'eccezione non gestita nel **codice Decode** o **LibraryCode** , il debugger interrompe sempre l'esecuzione.

Se si verifica un'eccezione non gestita in **UnrelatedCode**e il **codice** o **LibraryCode** è nello stack di chiamate, il debugger si interrompe.

Se le eccezioni first-chance sono abilitate per l'eccezione e l'eccezione si verifica in **LibraryCode** o **UnrelatedCode**:

- Se l'eccezione è gestita, il debugger non si interrompe.
- Se l'eccezione non è gestita, il debugger si interrompe.

### <a name="customize-javascript-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a>Personalizzare Just My Code JavaScript

Per categorizzare il codice utente e non utente per un singolo progetto JavaScript, è possibile aggiungere un file con *estensione JSON* denominato *mycode.js* alla cartella radice del progetto.

Le specifiche in questo file sostituiscono le classificazioni predefinite e il *mycode.default.wwa.jssu* file. Impossibile elencare tutte le coppie chiave-valore nel *mycode.js* del file. Il **codice**, le **librerie**e i valori non **correlati** possono essere matrici vuote.

*Mycode.jsnei* file usare questa sintassi:

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

|Nome|Description|
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

|Nome|Description|
|-|-|
|**MyCode**|Matrice di URL o di file classificati come **MyCode**.|
|**Raccolte**|Matrice di URL o di file classificati come **LibraryCode**.|
|**Unrelated**|Matrice di URL o di file classificati come **UnrelatedCode**.|

La stringa dell'URL o del file può contenere uno o più `*` caratteri, che corrispondono a zero o più caratteri. `*`corrisponde all'espressione regolare `.*` .
