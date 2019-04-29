---
title: Eseguire il debug con Just My Code il codice utente | Microsoft Docs
ms.date: 02/13/2019
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edb78ed49add85b35f3fb89b4ba424d44f52bf8b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905784"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Eseguire il debug con Just My Code solo il codice utente

*Just My Code* è una funzionalità di debug di Visual Studio automaticamente passaggi chiamate al sistema, framework e altro codice non utente. Nel **Stack di chiamate** finestra, Just My Code comprime tali chiamate nel **[codice esterno]** frame.

Just My Code funziona in modo diverso nei progetti .NET Framework, C++ e JavaScript.

## <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Abilitare o disabilitare Just My Code

Per la maggior parte dei linguaggi di programmazione, Just My Code è abilitato per impostazione predefinita.

- Per abilitare o disabilitare Just My Code in Visual Studio, sotto **degli strumenti** > **opzioni** (o **Debug** > **opzioni**) > **Debugging** > **generali**, selezionare o deselezionare **Abilita Just My Code**.

![Abilitare Just My Code nella finestra di dialogo Opzioni](../debugger/media/dbg_justmycode_options.png "Abilita Just My Code")

> [!NOTE]
> **Abilitare Just My Code** è un'impostazione globale che si applica a tutti i progetti di Visual Studio in tutte le lingue.

## <a name="just-my-code-debugging"></a>debug Just My Code

Durante una sessione di debug, il **moduli** Mostra finestra che il debugger viene considerato My Code (codice utente), moduli di codice insieme ai relativi simboli caricamento dello stato. Per altre informazioni, vedere [acquisire maggiore familiarità con la modalità con cui il debugger si connette all'app](../debugger/debugger-tips-and-tricks.md#modules_window).

![Il codice utente nella finestra di moduli](../debugger/media/dbg_justmycode_module.png "codice utente nella finestra moduli")

Nel **Stack di chiamate** oppure **attività** finestra, Just My Code consente di comprimere il codice non utente in un frame di grigio codice annotato con etichettato `[External Code]`.

![Frame di codice esterno nella finestra Stack di chiamate](../debugger/media/dbg_justmycode_externalcode.png "frame di codice esterno")

>[!TIP]
>Per aprire la **moduli**, **Stack di chiamate**, **le attività**, o la maggior parte delle altre finestre di debug, è necessario essere in una sessione di debug. Durante il debug, sotto **Debug** > **Windows**, selezionare windows che si desidera aprire.

<a name="BKMK_Override_call_stack_filtering"></a> Per visualizzare il codice in un compressa **[codice esterno]** frame, fare doppio clic nella **Stack di chiamate** oppure **attività** finestra e selezionare **Mostra codice esterno**dal menu di scelta rapida. Sostituire le righe di codice esterni espanso il **[codice esterno**] frame.

![Mostra codice esterno nella finestra Stack di chiamate](../debugger/media/dbg_justmycode_showexternalcode.png "Mostra codice esterno")

> [!NOTE]
> **Mostra codice esterno** è un profiler utente corrente, l'impostazione che si applica a tutti i progetti in tutti i linguaggi aperti dall'utente.

Fare doppio clic su una riga di codice esterno espanso nel **Stack di chiamate** finestra evidenzia la riga del codice chiamante in verde nel codice sorgente. Per le DLL o altri moduli non trovato o caricato, un simbolo o un'origine non trovato potrebbe aperta la pagina.

## <a name="BKMK__NET_Framework_Just_My_Code"></a> Just My Code in .NET Framework

Nei progetti .NET Framework, Just My Code Usa simboli (*PDB*) i file e ottimizzazioni del programma per classificare il codice utente e non utente. Il debugger di .NET Framework considera i file binari ottimizzati e non caricati *PDB* file di codice non utente.

Tre attributi del compilatore influiscono anche su ciò che il debugger .NET considera come codice utente:

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> indica al debugger che il codice di che cui è applicato non è codice utente.
- <xref:System.Diagnostics.DebuggerHiddenAttribute> nasconde il codice al debugger, anche se Just My Code è disattivato.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> indica al debugger di eseguire il codice che viene applicato, anziché eseguire tutto il codice.

Il debugger di .NET Framework considera tutto l'altro codice codice utente.

Durante il debug di .NET Framework

- **Eseguire il debug** > **Esegui istruzione** (o **F11**) nel codice non utente esegue le istruzioni di codice alla riga successiva del codice utente.
- **Eseguire il debug** > **Esci** (o **MAIUSC**+**F11**) in codice non utente in esecuzione alla riga successiva del codice utente.

Se non è presente codice utente più, il debug continua finché non termina, raggiunge un altro punto di interruzione o viene generato un errore.

<a name="BKMK_NET_Breakpoint_behavior"></a> Se il debugger si interrompe nel codice non utente (ad esempio, si utilizza **Debug** > **Interrompi tutto** e pause nel codice non utente), il **Nessuna origine** verrà visualizzata la finestra. È quindi possibile usare una **Debug** > **passaggio** comando per passare alla riga successiva del codice utente.

Se si verifica un'eccezione non gestita nel codice non utente, il debugger si interrompe alla riga di codice utente in cui è stato generato l'eccezione.

Se eccezioni first-chance sono abilitate per l'eccezione, la riga di codice utente chiamante viene evidenziata in verde nel codice sorgente. Il **Stack di chiamate** finestra vengono visualizzati i frame annotato con etichettato **[codice esterno]**.

## <a name="BKMK_C___Just_My_Code"></a> Just My Code in C++

A partire da Visual Studio 2017 versione 15.8, Just My Code per il codice è inoltre supportata l'esecuzione di istruzioni. Questa funzionalità richiede anche l'uso del [/JMC (solo il debug del codice)](/cpp/build/reference/jmc) opzione del compilatore. L'opzione è abilitata per impostazione predefinita in C++ progetti. Per la **Stack di chiamate** finestra e stack di chiamate supporto in Just My Code, il commutatore /JMC non è necessario.

<a name="BKMK_CPP_User_and_non_user_code"></a> Per essere classificato come codice utente, il file PDB per il file binario che contiene il codice utente deve essere caricato dal debugger (usare il **moduli** finestra per selezionare questa opzione).

Per il comportamento dello stack di chiamate, ad esempio nel **Stack di chiamate** Just My Code nella finestra C++ vengono considerate solo le funzioni *codice non utente*:

- Funzioni con informazioni di origine rimosse nei propri file di simboli.
- Funzioni i cui file di simboli indicano che non esiste alcun file di origine corrispondente allo stack frame.
- Funzioni specificate nei  *\*con estensione natjmc* i file nei *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* cartella.

Per il comportamento di avanzamento nell'esecuzione di codice, Just My Code in C++ prende in considerazione solo le funzioni *codice non utente*:

- Funzioni per il quale il file PDB corrispondente non è stato caricato nel debugger.
- Funzioni specificate nei  *\*con estensione natjmc* i file nei *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* cartella.

> [!NOTE]
> Per il supporto di avanzamento nell'esecuzione di codice in Just My Code, C++ codice deve essere compilato con i compilatori MSVC in Visual Studio 15.8 Preview 3 o versione successiva, e deve essere abilitata l'opzione del compilatore /JMC (è abilitata per impostazione predefinita). Per altre informazioni, vedere [Personalizza C++ stack di chiamate e comportamento dell'esecuzione di codice](#BKMK_CPP_Customize_call_stack_behavior)) e ciò [post di blog](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/). Per il codice compilato usando un compilatore precedente, *con estensione natstepfilter* file sono l'unico modo per personalizzare l'esecuzione di istruzioni, il codice indipendente dalla Just My Code. Visualizzare [Personalizza C++ comportamento di debug passo a passo](#BKMK_CPP_Customize_stepping_behavior).

<a name="BKMK_CPP_Stepping_behavior"></a> Durante il debug in C++:

- **Eseguire il debug** > **Esegui istruzione** (o **F11**) nel codice non utente esegue le istruzioni di codice alla riga successiva del codice utente.
- **Eseguire il debug** > **Esci** (o **MAIUSC**+**F11**) in codice non utente in esecuzione alla riga successiva del codice utente.

Se non è presente codice utente più, il debug continua finché non termina, raggiunge un altro punto di interruzione o viene generato un errore.

Se il debugger si interrompe nel codice non utente (ad esempio, si utilizza **Debug** > **Interrompi tutto** e sospendere le risorse in codice non utente), l'esecuzione continua del codice non utente.

Se il debugger raggiunge un'eccezione, si ferma sull'eccezione, se è in codice utente o non utente. **Non gestite dall'utente** le opzioni presenti nella **impostazioni eccezioni** vengono ignorati nella finestra di dialogo.

### <a name="BKMK_CPP_Customize_call_stack_behavior"></a> Personalizzare C++ stack di chiamate e comportamento dell'esecuzione del codice

Per i progetti C++, è possibile specificare i moduli, i file di origine e le funzioni di **Stack di chiamate** trattata come codice non utente nella finestra specificandoli nei  *\*con estensione natjmc* file. Questa personalizzazione può essere applicata anche al codice l'esecuzione di istruzioni se si usa il compilatore più recente (vedere [ C++ Just My Code](#BKMK_CPP_User_and_non_user_code)).

- Per specificare il codice non utente per tutti gli utenti del computer che esegue Visual Studio, aggiungere il file con estensione *natjmc* alla cartella *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers*.
- Per specificare il codice non utente per un singolo utente, aggiungere il *con estensione natjmc* del file per il *documenti %USERPROFILE%\My\\< versione di Visual Studio\>\Visualizers* cartella.

Oggetto *con estensione natjmc* file è un file XML con questa sintassi:

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
|`Name`|Obbligatorio. Percorso completo del modulo o dei moduli. È possibile usare i caratteri jolly di Windows `?` (zero o un carattere) e `*` (zero o più caratteri). Ad esempio,<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> indica al debugger di considerare tutti i moduli nella cartella *\3rdParty\UtilLibs* di qualsiasi unità come codice esterno.|
|`Company`|Facoltativo. Nome della società che pubblica il modulo che viene incorporato nel file eseguibile. È possibile utilizzare questo attributo per evitare ambiguità tra i moduli.|

 **Attributi dell'elemento file**

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Obbligatorio. Percorso completo del file o dei file di codice sorgente da considerare come codice esterno. È possibile usare i caratteri jolly di Windows `?` e `*` quando si specifica il percorso.|

 **Attributi dell'elemento funzione**

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Obbligatorio. Nome completo della funzione da considerare come codice esterno.|
|`Module`|Facoltativo. Nome o percorso completo del modulo che contiene la funzione. È possibile utilizzare questo attributo per evitare ambiguità tra funzioni con lo stesso nome.|
|`ExceptionImplementation`|Se impostato su `true`, lo stack di chiamate mostra la funzione che ha generato l'eccezione anziché questa funzione.|

### <a name="BKMK_CPP_Customize_stepping_behavior"></a> Personalizzare C++ comportamento dell'esecuzione indipendente dalle impostazioni di Just My Code

Nei progetti C++, è possibile specificare le funzioni per eseguire failover elencandoli come codice non utente nei  *\*con estensione natstepfilter* file. Funzioni elencate nelle  *\*con estensione natstepfilter* file non sono interdipendenti impostazioni Just My Code.

- Per specificare il codice non utente per tutti gli utenti di Visual Studio locali, aggiungere il *con estensione natstepfilter* del file per il *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* cartella.
- Per specificare il codice non utente per un singolo utente, aggiungere il *con estensione natstepfilter* del file per il *documenti %USERPROFILE%\My\\< versione di Visual Studio\>\Visualizers* cartella.

Oggetto *con estensione natstepfilter* file è un file XML con questa sintassi:

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
|`Module`|Facoltativo. Espressione regolare formattata in base a ECMA-262 che specifica il percorso completo del modulo che contiene la funzione. La corrispondenza non fa distinzione tra maiuscole e minuscole.|
|`Action`|Obbligatorio. Uno dei valori seguenti (viene effettuata la distinzione tra maiuscole e minuscole):<br /><br /> `NoStepInto`  -indica al debugger di ignorare la funzione.<br /> `StepInto`  -indica al debugger di eseguire l'istruzione della funzione, eseguendo l'override di qualsiasi altro `NoStepInto` per la funzione corrispondente.|

## <a name="BKMK_JavaScript_Just_My_Code"></a> Just My Code in JavaScript

<a name="BKMK_JS_User_and_non_user_code"></a> Just My Code in JavaScript controlla l'esecuzione e la visualizzazione dello stack di chiamate suddividendo il codice in una delle classificazioni seguenti:

|||
|-|-|
|**MyCode**|Codice utente che si possiede e si controlla.|
|**LibraryCode**|Codice non utente da librerie utilizzate regolarmente e l'app si basa su a funzionare correttamente (ad esempio WinJS o jQuery).|
|**UnrelatedCode**|Codice non utente nelle app che non si è proprietari e l'app non si basa sul corretto funzionamento. Ad esempio, un SDK che consente di visualizzare annunci pubblicitari potrebbe essere UnrelatedCode. Nei progetti UWP, qualsiasi codice che viene caricato in un'app da un URI HTTP o HTTPS viene anche considerato UnrelatedCode.|

Il debugger JavaScript classifica codice come utente o non utente in questo ordine:

1. Le classificazioni predefinite.
   - Script eseguito passando una stringa alla fornita dall'host `eval` funzione viene **MyCode**.
   - Script eseguito passando una stringa per il `Function` costruttore viene **LibraryCode**.
   - Lo script in un riferimento a framework, ad esempio WinJS o Azure SDK, è **LibraryCode**.
   - Script eseguito passando una stringa per il `setTimeout`, `setImmediate`, o `setInterval` funzioni viene **UnrelatedCode**.

2. Le classificazioni specificate per tutti i progetti JavaScript di Visual Studio il *%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json* file.

3. Le classificazioni nel *mycode.json* file del progetto corrente.

Ogni passaggio di classificazione esegue l'override dei passaggi precedenti.

Tutto il resto del codice viene classificato come **MyCode**.

È possibile modificare le classificazioni predefinite e classificare file specifici e gli URL come codice utente o non utente, aggiungendo un *. JSON* file denominato *mycode.json* nella cartella radice di un progetto di JavaScript. Visualizzare [personalizzare Just My Code in JavaScript](#BKMK_JS_Customize_Just_My_Code).

<a name="BKMK_JS_Stepping_behavior"></a> Durante il debug di JavaScript:

- Se il codice non utente, una funzione **Debug** > **Esegui istruzione** (o **F11**) si comporta come **Debug**  >  **Esegui istruzione/routine** (o **F10**).
- Se un'esecuzione inizia nel non utente (**LibraryCode** oppure **UnrelatedCode**) codice, l'esecuzione temporanea si comporta come se Just My Code non è abilitata. Quando si esegue nuovamente codice utente, Just My Code per il debug è abilitato nuovamente.
- Quando un utente codice passaggio comporta l'uscita dal contesto di esecuzione corrente, il debugger si arresta alla riga di codice utente eseguita successiva. Se ad esempio un callback viene eseguito nel codice **LibraryCode**, il debugger continua finché la riga di codice utente successiva non viene eseguita.
- **Esci da istruzione /** (o **MAIUSC**+**F11**) si interrompe nella riga successiva del codice utente.

Se non è presente codice utente più, il debug continua finché non termina, raggiunge un altro punto di interruzione o viene generato un errore.

Punti di interruzione impostati nel codice vengono sempre raggiunti, ma il codice viene classificato.

- Se il `debugger` parola chiave viene visualizzata **LibraryCode**, il debugger si interrompe sempre.
- Se il `debugger` parola chiave viene visualizzata **UnrelatedCode**, il debugger non si arresta.

<a name="BKMK_JS_Exception_behavior"></a> Se si verifica un'eccezione non gestita nel **MyCode** oppure **LibraryCode** codice, il debugger si interrompe sempre.

Se si verifica un'eccezione non gestita nel **UnrelatedCode**, e **MyCode** oppure **LibraryCode** è nello stack di chiamate, il debugger si interrompe.

Se le eccezioni first-chance sono abilitate per l'eccezione e l'eccezione si verifica nelle **LibraryCode** oppure **UnrelatedCode**:

- Se l'eccezione è gestita, il debugger non si interrompe.
- Se l'eccezione non è gestita, il debugger si interrompe.

### <a name="BKMK_JS_Customize_Just_My_Code"></a> Personalizzare Just My Code in JavaScript

Per classificare il codice utente e non utente per un singolo progetto di JavaScript, è possibile aggiungere un *. JSON* file denominato *mycode.json* nella cartella radice del progetto.

In questo file specifiche di eseguire l'override le classificazioni predefinite e il *mycode.default.wwa.json* file. Il *mycode.json* file non è necessario elencare tutte le coppie chiave-valore. Il **MyCode**, **librerie**, e **Unrelated** i valori possono essere matrici vuote.

*MyCode.JSON* file utilizzano questa sintassi:

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

|||
|-|-|
|**Eval**|Script eseguito passando una stringa alla funzione `eval` fornita dall'host. Per impostazione predefinita, lo script Eval viene classificato come **MyCode**.|
|**Function**|Script eseguito passando una stringa al costruttore `Function`. Per impostazione predefinita, lo script Function viene classificato come **LibraryCode**.|
|**ScriptBlock**|Script eseguito passando una stringa alla funzione `setTimeout`, `setImmediate` o `setInterval`. Per impostazione predefinita, lo script ScriptBlock viene classificato come **UnrelatedCode**.|

È possibile modificare il valore a una delle parole chiave seguenti:

- `MyCode` classifica lo script come **MyCode**.
- `Library` classifica lo script come **LibraryCode**.
- `Unrelated` classifica lo script come **UnrelatedCode**.

**MyCode, Libraries e Unrelated**

Le coppie chiave-valore **MyCode**, **Libraries** e **Unrelated** specificano gli URL o i file da includere in una classificazione:

|||
|-|-|
|**MyCode**|Matrice di URL o di file classificati come **MyCode**.|
|**Libraries**|Matrice di URL o di file classificati come **LibraryCode**.|
|**Unrelated**|Matrice di URL o di file classificati come **UnrelatedCode**.|

La stringa URL o del file può contenere uno o più `*` caratteri, che corrispondono a zero o più caratteri. `*` equivale all'espressione regolare `.*`.
