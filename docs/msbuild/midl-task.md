---
title: Attività MIDL | Microsoft Docs
description: Informazioni sull'attività MIDL MSBuild, che esegue il wrapping dello strumento Microsoft Interface Definition Language (MIDL), midl.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.TypeLibFormat
- vc.task.midl
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), MIDL task
- MIDL task (MSBuild (C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 89d9469c2e81572f66a70b5f61881b4baa9fde68
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108668"
---
# <a name="midl-task"></a>MIDL (attività)

Esegue il wrapping dello strumento compilatore MIDL (Microsoft Interface Definition Language), *midl.exe*. Per altre informazioni, vedere [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

## <a name="parameters"></a>Parametri

 Di seguito sono descritti i parametri dell'attività **MIDL**. La maggior parte dei parametri di attività e alcuni set di parametri corrispondono a un'opzione della riga di comando.

- **AdditionalIncludeDirectories**

     Parametro **Facoltativo String[].**

     Aggiunge una directory all'elenco di directory nelle quali viene effettuata la ricerca dei file IDL importati, inclusi i file di intestazione e i file di configurazione dell'applicazione.

     Per altre informazioni, vedere l'opzione **/I** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **AdditionalOptions**

     Parametro **String** facoltativo.

     Elenco di opzioni della riga di comando. Ad esempio, / \<option1>  / \<option2>  / \<option#> . Usare questo parametro per specificare le opzioni della riga di comando che non sono rappresentate da altri parametri dell'attività MIDL.

     Per altre informazioni, vedere [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **ApplicationConfigurationMode**

     Parametro **booleano** facoltativo.

     Se `true`, consente di usare alcune parole chiave dei file di configurazione dell'applicazione nel file IDL.

     Per altre informazioni, vedere l'opzione **/app_config** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **ClientStubFile**

     Parametro **String** facoltativo.

     Specifica il nome del file stub client per un'interfaccia RPC.

     Per altre informazioni, vedere l'opzione **/cstub** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL). Vedere anche il parametro **ServerStubFile** in questa tabella.

- **CPreprocessOptions**

     Parametro **String** facoltativo.

     Specifica le opzioni da passare al preprocessore C/C++. Specificare un elenco di opzioni del preprocessore delimitate da spazio. Deve contenere `/E` l'opzione .

     Per altre informazioni, vedere l'opzione **/cpp_opt** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **DefaultCharType**

     Parametro **String** facoltativo.

     Specifica il tipo di carattere predefinito che verrà usato dal compilatore C per compilare il codice generato.

     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

    |Valore|Opzione da riga di comando|
    |-----------|--------------------------|
    |**Firmato**|**/char signed**|
    |**Senza segno**|**/char unsigned**|
    |**Ascii**|**/char ascii7**|

     Per altre informazioni, vedere l'opzione **/char** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **DllDataFileName**

     Parametro **String** facoltativo.

     Specifica il nome file per il file *dlldata* generato per una DLL del proxy.

     Per altre informazioni, vedere l'opzione **/dlldata** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **EnableErrorChecks**

     Parametro **String** facoltativo.

     Specifica il tipo di controllo errori che verrà eseguito dagli stub generati in fase di esecuzione.

     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

    |Valore|Opzione da riga di comando|
    |-----------|--------------------------|
    |**Nessuno**|**/error none**|
    |**EnableCustom**|**/error**|
    |**Tutto**|**/error all**|

     Per altre informazioni, vedere l'opzione **/error** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **ErrorCheckAllocations**

     Parametro **booleano** facoltativo.

     Se `true`, verifica la presenza di errori di memoria insufficiente.

     Per altre informazioni, vedere l'opzione **/error allocation** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **ErrorCheckBounds**

     Parametro **booleano** facoltativo.

     Se `true`, controlla le dimensioni delle matrici variabili conformi e variabili rispetto alla specifica relativa alla durata delle trasmissioni.

     Per altre informazioni, vedere l'opzione **/error bounds_check** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **ErrorCheckEnumRange**

     Parametro **booleano** facoltativo.

     Se `true`, controlla che i valori di enumerazione siano compresi in un intervallo consentito.

     Per altre informazioni, vedere l'opzione **/error enum** nella guida della riga di comando (**/?**) per *midl.exe*.

- **ErrorCheckRefPointers**

     Parametro **booleano** facoltativo.

     Se `true`, controlla che nessun puntatore di riferimento Null venga passato agli stub client.

     Per altre informazioni, vedere l'opzione **/error ref** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **ErrorCheckStubData**

     Parametro **booleano** facoltativo.

     Se `true`, genera uno stub che acquisisce eccezioni di unmarshalling sul lato server e le propaga al client.

     Per altre informazioni, vedere l'opzione **/error stub_data** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **GenerateClientFiles**

     Parametro **String** facoltativo.

     Specifica se il compilatore genera un file di origine C sul lato client per un'interfaccia RPC.

     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

    |Valore|Opzione da riga di comando|
    |-----------|--------------------------|
    |**Nessuno**|**/client none**|
    |**Stub**|**/client stub**|

     Per altre informazioni, vedere l'opzione **/client** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **GenerateServerFiles**

     Parametro **String** facoltativo.

     Specifica se il compilatore genera un file di origine C sul lato server per un'interfaccia RPC.

     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

    |Valore|Opzione da riga di comando|
    |-----------|--------------------------|
    |**Nessuno**|**/server none**|
    |**Stub**|**/server stub**|

     Per altre informazioni, vedere l'opzione **/server** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **GenerateStublessProxies**

     Parametro **booleano** facoltativo.

     Se `true`, genera stub completamente interpretati con proxy senza stub per le interfacce degli oggetti.

     Per altre informazioni, vedere l'opzione **/Oicf** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **GenerateTypeLibrary**

     Parametro **booleano** facoltativo.

     Se `true`, non viene generato un file di libreria dei tipi (file con estensione *tlb*).

     Per altre informazioni, vedere l'opzione **/notlb** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **HeaderFileName**

     Parametro **String** facoltativo.

     Specifica il nome del file di intestazione generato.

     Per altre informazioni, vedere l'opzione **/h** oppure **/header** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **IgnoreStandardIncludePath**

     Parametro **booleano** facoltativo.

     Se `true`, l'attività MIDL effettua la ricerca solo nelle directory specificate usando l'opzione **AdditionalIncludeDirectories** e ignora la directory corrente e le directory specificate dalla variabile di ambiente INCLUDE.

     Per altre informazioni, vedere l'opzione **/no_def_idir** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **InterfaceIdentifierFileName**

     Parametro **String** facoltativo.

     Specifica il nome del *file dell'identificatore di interfaccia* per un'interfaccia COM. Esegue l'override del nome predefinito ottenuto aggiungendo "_i.c" al nome file IDL.

     Per altre informazioni, vedere l'opzione **/iid** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **LocaleID**

     Parametro **int** facoltativo.

     Specifica l'*identificatore delle impostazioni locali* che consente l'uso di caratteri internazionali in file di input, nomi file e percorsi di directory. Specificare un identificatore delle impostazioni locali decimale.

     Per altre informazioni, vedere l'opzione **/lcid** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL). Vedere anche [Identificatori delle impostazioni locali](/windows/desktop/intl/locale-identifiers).

- **MkTypLibCompatible**

     Parametro **booleano** facoltativo.

     Se `true`, è necessario che il formato dei file di input sia compatibile con *mktyplib.exe* versione 2.03.

     Per altre informazioni, vedere l'opzione **/mktyplib203** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL). Vedere anche [ODL file syntax](/previous-versions/windows/desktop/automat/odl-file-syntax) (Sintassi del file ODL) nel sito Web MSDN.

- **OutputDirectory**

     Parametro **String** facoltativo.

     Specifica la directory predefinita in cui l'attività MIDL scrive i file di output.

     Per altre informazioni, vedere l'opzione **/out** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **PreprocessorDefinitions**

     Parametro **String[]** facoltativo.

     Specifica una o più *definizioni*, ovvero un nome e un valore facoltativo da passare al preprocessore C come in base alla direttiva `#define`. Il formato di ogni definizione è *nome[=valore]*.

     Per altre informazioni, vedere l'opzione **/D** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL). Vedere anche il parametro **UndefinePreprocessorDefinitions** in questa tabella.

- **ProxyFileName**

     Parametro **String** facoltativo.

     Specifica il nome del file proxy di interfaccia per un'interfaccia COM.

     Per altre informazioni, vedere l'opzione **/proxy** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **RedirectOutputAndErrors**

     Parametro **String** facoltativo.

     Reindirizza l'output, ad esempio messaggi di errore e avvisi, dall'output standard al file specificato.

     Per altre informazioni, vedere l'opzione **/o** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **ServerStubFile**

     Parametro **String** facoltativo.

     Specifica il nome del file stub server per un'interfaccia RPC.

     Per altre informazioni, vedere l'opzione **/sstub** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL). Vedere anche il parametro **ClientStubFile** in questa tabella.

- **Origine**

     Parametro `ITaskItem[]` obbligatorio.

     Specifica un elenco dei file di origine separati da spazi.

- **StructMemberAlignment**

     Parametro **String** facoltativo.

     Specifica l'allineamento (*livello di compressione*) delle strutture nel sistema di destinazione.

     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

    |Valore|Opzione da riga di comando|
    |-----------|--------------------------|
    |**NotSet**|*\<none>*|
    |**1**|**/Zp1**|
    |**2**|**/Zp2**|
    |**4**|**/Zp4**|
    |**8**|**/Zp8**|

     Per altre informazioni, vedere l'opzione **/Zp** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL). L'opzione **/Zp** equivale all'opzione **/pack** e all'opzione **/align** precedente.

- **SuppressCompilerWarnings**

     Parametro **booleano** facoltativo.

     Se `true`, elimina i messaggi di avviso dall'attività MIDL.

     Per altre informazioni, vedere l'opzione **/no_warn** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **SuppressStartupBanner**

     Parametro `Boolean` facoltativo.

     Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.

     Per altre informazioni, vedere l'opzione **/nologo** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **TargetEnvironment**

     Parametro **String** facoltativo.

     Specifica l'ambiente in cui viene eseguita l'applicazione.

     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

    |Valore|Opzione da riga di comando|
    |-----------|--------------------------|
    |**NotSet**|*\<none>*|
    |**Win32**|**/env win32**|
    |**Itanium**|**/env ia64**|
    |**X64**|**/env x64**|

     Per altre informazioni, vedere l'opzione **/env** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **TrackerLogDirectory**

     Parametro `String` facoltativo.

     Specifica la directory intermedia in cui sono archiviati i log di rilevamento per questa attività.

- **TypeLibFormat**

     Parametro **String** facoltativo.

     Specifica il formato del file di libreria dei tipi.

     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

    |Valore|Opzione da riga di comando|
    |-----------|--------------------------|
    |**NewFormat**|**/newtlb**|
    |**OldFormat**|**/oldtlb**|

     Per altre informazioni, vedere le opzioni **/newtlb** e **/oldtlb** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **TypeLibraryName**

     Parametro **String** facoltativo.

     Specifica il nome del file di libreria dei tipi.

     Per altre informazioni, vedere l'opzione **/tlb** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **UndefinePreprocessorDefinitions**

     Parametro **String[]** facoltativo.

     Rimuove le definizioni precedenti di un nome passando il nome al preprocessore C come in base a una direttiva `#undefine`. Specificare uno o più nomi definiti in precedenza.

     Per altre informazioni, vedere l'opzione **/U** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL). Vedere anche il parametro **PreprocessorDefinitions** in questa tabella.

- **ValidateAllParameters**

     Parametro `Boolean` facoltativo.

     Se `true`, genera altre informazioni di controllo errore usate per eseguire controlli integrità in fase di esecuzione. Se `false`, le informazioni di controllo errore non vengono generate.

     Per altre informazioni, vedere le opzioni **/robust** e **/no_robust** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL).

- **WarnAsError**

     Parametro `Boolean` facoltativo.

     Se `true`, tutti gli avvisi vengono considerati come errori.

     Se il parametro dell'attività MIDL **WarningLevel** non viene specificato, gli avvisi a livello predefinito, ovvero il livello 1, vengono considerati come errori.

     Per altre informazioni, vedere l'opzione **/WX** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL). Vedere anche il parametro **WarningLevel** in questa tabella.

- **WarningLevel**

     Parametro **String** facoltativo.

     Specifica la gravità (*livello di avviso*) degli avvisi da creare. Per il valore 0 non vengono creati avvisi. Diversamente, viene creato un avviso se il livello di avviso è numericamente inferiore o uguale al valore specificato.

     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

    |Valore|Opzione da riga di comando|
    |-----------|--------------------------|
    |**0**|**/W0**|
    |**1**|**/W1**|
    |**2**|**/W2**|
    |**3**|**/W3**|
    |**4**|**/W4**|

     Per altre informazioni, vedere l'opzione **/W** in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference) (Informazioni di riferimento sulla riga di comando MIDL). Vedere anche il parametro **WarnAsError** in questa tabella.

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
