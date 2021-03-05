---
title: Opzioni della riga di comando di VSTest.Console.exe
description: Informazioni sul VSTest.Console.exe strumento da riga di comando che esegue i test. Questo articolo include le opzioni generali della riga di comando.
ms.custom: SEO-VS-2020
ms.date: 07/17/2020
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: mikejo
author: mikejo5000
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 86544ad36874ec2a99fac0f8505b24548e83c7c0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168361"
---
# <a name="vstestconsoleexe-command-line-options"></a>Opzioni della riga di comando di VSTest.Console.exe

*VSTest.Console.exe* è lo strumento da riga di comando per l'esecuzione di test. È possibile specificare diverse opzioni in qualsiasi ordine nella riga di comando. Queste opzioni sono elencate in [Opzioni generali della riga di comando](#general-command-line-options).

> [!NOTE]
> Per la compatibilità, l'adapter MSTest in Visual Studio funziona anche in modalità legacy (equivalente all'esecuzione di test con *mstest.exe*). In modalità legacy non può usufruire della funzionalità TestCaseFilter. L'adapter può passare alla modalità legacy quando è specificato un file *testsettings*, **forcelegacymode** è impostato su **true** in un file *runsettings* oppure usando attributi quali **HostType**.
>
> Per eseguire test automatizzati in un computer basato su architettura ARM è necessario usare *VSTest.Console.exe*.

Aprire [prompt dei comandi per gli sviluppatori](../ide/reference/command-prompt-powershell.md) per usare lo strumento da riga di comando. in alternativa, è possibile trovare lo strumento in *% Program Files (x86)% \ Microsoft Visual Studio \\<versione \> \\<Edition \> \common7\ide\CommonExtensions \\<Platform | Microsoft>*.

## <a name="general-command-line-options"></a>Opzioni generali della riga di comando

Nella tabella seguente vengono illustrate tutte le opzioni di *VSTest.Console.exe* con una breve descrizione. È possibile visualizzare un riepilogo simile digitando `VSTest.Console/?` a una riga di comando.

| Opzione | Descrizione |
|---|---|
|**[*nomi file di test*]**|Esegue i test dai file specificati. Per separare i nomi di file di test, usare gli spazi.<br />Esempi: `mytestproject.dll`, `mytestproject.dll myothertestproject.exe`|
|**/Settings:[*nome file*]**|Eseguire i test con ulteriori impostazioni, ad esempio gli agenti di raccolta dati. Per ulteriori informazioni, vedere [configurare unit test utilizzando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)<br />Esempio: `/Settings:local.runsettings`|
|**/Tests:[*nome test*]**|Esegue i test con nomi che contengono i valori specificati. Per fornire più valori, separarli con virgole.<br />Esempio: `/Tests:TestMethod1,testMethod2`<br />Non è possibile usare l'opzione della riga di comando **/Tests** con l'opzione della riga di comando **/TestCaseFilter**.|
|**/Parallel**|Specifica che i test devono essere eseguiti in parallelo. Per impostazione predefinita, è possibile usare fino a tutti i core disponibili nel computer. È possibile configurare il numero di core da usare in un file di impostazioni.|
|**/Enablecodecoverage**|Abilita l'adapter dei dati di diagnostica CodeCoverage nell'esecuzione dei test.<br />Usare le impostazioni predefinite se non diversamente specificato usando un file di impostazioni.|
|**/InIsolation**|Esegue i test in un processo isolato.<br />L'isolamento rende meno probabile l'arresto del processo *vstest.console.exe* in caso di errore nei test, ma questi ultimi potrebbero essere più lenti.|
|**/UseVsixExtensions**|Questa opzione consente al processo *vstest.console.exe* di usare o ignorare le eventuali estensioni VSIX installate nell'esecuzione dei test.<br />Questa opzione è deprecata. È possibile che a partire dalla prossima versione principale di Visual Studio questa opzione venga rimossa. Passare all'uso delle estensioni rese disponibili come pacchetto NuGet.<br />Esempio: `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*percorso*]**|Impone al processo *vstest.console.exe* l'uso di adattatori di test personalizzati in un percorso specificato (se disponibili) nell'esecuzione dei test.<br />Esempio: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform:[*tipo di piattaforma*]**|Impone l'uso della piattaforma specificata, invece della piattaforma determinata dal runtime corrente. Questa opzione è in grado di forzare solo piattaforme x86 e x64 in Windows. L'opzione ARM è interruppe e il risultato sarà x64 nella maggior parte dei sistemi.<br />Non specificare questa opzione per l'esecuzione in Runtime non inclusi nell'elenco di valori validi, ad esempio ARM64.<br />I valori validi sono x86, x64 e ARM.<br /> 
|**/Framework: [*versione framework*]**|Versione .NET di destinazione da usare per l'esecuzione dei test.<br />Esempi di valori sono `Framework35`, `Framework40`, `Framework45`, `FrameworkUap10`, `.NETCoreApp,Version=v1.1`.<br />TargetFrameworkAttribute viene usato per rilevare automaticamente questa opzione dall'assembly e il valore predefinito è `Framework40` quando l'attributo non è presente. È necessario specificare questa opzione in modo esplicito se si rimuove il [TargetFrameworkAttribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) dagli assembly .NET Core.<br />Se il Framework di destinazione viene specificato come **Framework35**, i test vengono eseguiti in CLR 4,0 "modalità di compatibilità".<br />Esempio: `/Framework:framework40`|
|**/TestCaseFilter:[*espressione*]**|Esegue test corrispondenti all'espressione specificata.<br /><Expression\> è nel formato <property\>=<value\>[\|<Expression\>].<br />Esempio: `/TestCaseFilter:"Priority=1"`<br />Esempio: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />Non è possibile usare l'opzione della riga di comando **/TestCaseFilter** con l'opzione della riga di comando **/Tests**. <br />Per informazioni sulla creazione e sull'uso delle espressioni, vedere il [filtro TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).|
|**/?**|Visualizza le informazioni sull'utilizzo.|
|**/Logger:[*uri/nome descrittivo*]**|Specifica un logger per i risultati di test. Specificare il parametro più volte per abilitare più logger.<br />Esempio: per registrare i risultati in un file di Risultati test di Visual Studio (TRX), usare<br />**/Logger: TRX**<br />**[; LogFilename = \<Defaults to unique file name> ]**|
|**/ListTests:[*nome file*]**|Elenca i test individuati dal contenitore di test specificato.|
|**/ListDiscoverers**|Elenca gli agenti di individuazione test installati.|
|**/ListExecutors**|Elenca gli executor di test installati.|
|**/ListLoggers**|Elenca i logger di test installati.|
|**/ListSettingsProviders**|Elenca i provider di impostazioni test installati.|
|**/Blame**|Esegue i test in modalità di segnalazione degli errori. Questa opzione è utile per isolare i test problematici che provocano l'arresto anomalo dell'host di test. Quando viene rilevato un arresto anomalo del sistema, viene creato un file di sequenza in `TestResults/<Guid>/<Guid>_Sequence.xml` che acquisisce l'ordine dei test eseguiti prima dell'arresto anomalo. Per ulteriori informazioni, vedere [Blame Data Collector](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag:[*nome file*]**|Scrive i log di traccia di diagnostica nel file specificato.|
|**/ResultsDirectory:[*percorso*]**|Directory dei risultati dei test che verrà creata nel percorso specificato, se non esistente.<br />Esempio: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*ID processo padre*]**|ID del processo padre responsabile dell'avvio del processo corrente.|
|**/Port:[*porta*]**|La porta per la connessione socket e la ricezione dei messaggi di evento.|
|**/Collect:[*nome descrittivo agente di raccolta dati*]**|Abilita l'agente di raccolta dati per l'esecuzione dei test. [Ulteriori informazioni](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md).|

> [!TIP]
> Opzioni e valori non applicano la distinzione tra maiuscole e minuscole.

## <a name="examples"></a>Esempio

La sintassi per l'esecuzione di *vstest.console.exe* è la seguente:

`vstest.console.exe [TestFileNames] [Options]`

Il comando seguente esegue *vstest.console.exe* per la libreria di test *myTestProject.dll*:

```cmd
vstest.console.exe myTestProject.dll
```

Il comando seguente esegue *vstest.console.exe* con più file di test. Per separare i nomi di file di test, usare gli spazi:

```cmd
vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

Il comando seguente esegue *vstest.console.exe* con varie opzioni. Esegue i test indicati nel file *myTestFile.dll* in un processo isolato e usa le impostazioni specificate nel file *Local.RunSettings*. Esegue inoltre solo i test contrassegnati "Priority=1" e registra i risultati in un file con estensione *trx*.

```cmd
vstest.console.exe myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```

Il comando seguente esegue *vstest.console.exe* con l' `/blame` opzione per la libreria di test *myTestProject.dll*:

```cmd
vstest.console.exe myTestFile.dll /blame
```

Se si è verificato un arresto anomalo dell'host di test, viene generato il file di *sequence.xml* . Il file contiene i nomi completi dei test nella sequenza di esecuzione fino al test specifico che era in esecuzione al momento dell'arresto anomalo.

Se non è presente un arresto anomalo dell'host di test, il file di *sequence.xml* non verrà generato.

Esempio di un file di *sequence.xml* generato: 

```xml
<?xml version="1.0"?>
<TestSequence>
  <Test Name="TestProject.UnitTest1.TestMethodB" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
  <Test Name="TestProject.UnitTest1.TestMethodA" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
</TestSequence>
```
