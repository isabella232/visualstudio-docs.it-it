---
title: Opzioni della riga di comando di VSTest.Console.exe
ms.date: 07/12/2018
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: gewarren
author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8bf4cea6dcd87b8cf0d2113ac3a245163ba89080
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746923"
---
# <a name="vstestconsoleexe-command-line-options"></a>Opzioni della riga di comando di VSTest.Console.exe

*VSTest.Console.exe* è lo strumento da riga di comando per l'esecuzione di test. È possibile specificare diverse opzioni in qualsiasi ordine nella riga di comando. Queste opzioni sono elencate in [Opzioni generali della riga di comando](#general-command-line-options).

> [!NOTE]
> Per la compatibilità, l'adapter MSTest in Visual Studio funziona anche in modalità legacy (equivalente all'esecuzione di test con *mstest.exe*). In modalità legacy non può usufruire della funzionalità TestCaseFilter. L'adapter può passare alla modalità legacy quando è specificato un file *testsettings*, **forcelegacymode** è impostato su **true** in un file *runsettings* oppure usando attributi quali **HostType**.
>
> Per eseguire test automatizzati in un computer basato su architettura ARM è necessario usare *VSTest.Console.exe*.

## <a name="general-command-line-options"></a>Opzioni generali della riga di comando

Nella tabella seguente vengono illustrate tutte le opzioni di *VSTest.Console.exe* con una breve descrizione. È possibile visualizzare un riepilogo simile digitando `VSTest.Console/?` a una riga di comando.

| Opzione | Description |
|---|---|
|**[*nomi file di test*]**|Esegue i test dai file specificati. Per separare i nomi di file di test, usare gli spazi.<br />Esempi: `mytestproject.dll`, `mytestproject.dll myothertestproject.exe`|
|**/Settings:[*nome file*]**|Eseguire i test con ulteriori impostazioni, ad esempio gli agenti di raccolta dati.<br />Esempio: `/Settings:Local.RunSettings`|
|**/Tests:[*nome test*]**|Esegue i test con nomi che contengono i valori specificati. Per fornire più valori, separarli con virgole.<br />Esempio: `/Tests:TestMethod1,testMethod2`<br />Non è possibile usare l'opzione della riga di comando **/Tests** con l'opzione della riga di comando **/TestCaseFilter**.|
|**/Parallel**|Specifica che i test devono essere eseguiti in parallelo. Per impostazione predefinita, è possibile usare fino a tutti i core disponibili nel computer. Il numero di core da usare può essere configurato tramite un file di impostazioni.|
|**/Enablecodecoverage**|Abilita l'adapter dei dati di diagnostica CodeCoverage nell'esecuzione dei test.<br />Usare le impostazioni predefinite se non diversamente specificato usando un file di impostazioni.|
|**/InIsolation**|Esegue i test in un processo isolato.<br />L'isolamento rende meno probabile l'arresto del processo *vstest.console.exe* in caso di errore nei test, ma questi ultimi potrebbero essere più lenti.|
|**/UseVsixExtensions**|Questa opzione consente al processo *vstest.console.exe* di usare o ignorare le eventuali estensioni VSIX installate nell'esecuzione dei test.<br />Questa opzione è stata deprecata. È possibile che a partire dalla prossima versione principale di Visual Studio questa opzione venga rimossa. Passare all'uso delle estensioni rese disponibili come pacchetto NuGet.<br />Esempio: `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*percorso*]**|Impone al processo *vstest.console.exe* l'uso di adattatori di test personalizzati in un percorso specificato (se disponibili) nell'esecuzione dei test.<br />Esempio: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform:[*tipo di piattaforma*]**|Architettura della piattaforma di destinazione da usare per l'esecuzione del test.<br />I valori validi sono x86, x64 e ARM.|
|**/Framework: [*versione framework*]**|Versione di .NET di destinazione da utilizzare per l'esecuzione di test.<br />I valori validi sono Framework35, Framework40, Framework45 e FrameworkUap10.<br />Se il framework di destinazione è specificato come **Framework35**, i test vengono eseguiti in "modalità di compatibilità" CLR 4.0.<br />Esempio: `/Framework:framework40`|
|**/TestCaseFilter:[*espressione*]**|Esegue test corrispondenti all'espressione specificata.<br /><Expression\> è nel formato <property\>=<value\>[\|<Expression\>].<br />Esempio: `/TestCaseFilter:"Priority=1"`<br />Esempio: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />Non è possibile usare l'opzione della riga di comando **/TestCaseFilter** con l'opzione della riga di comando **/Tests**. <br />Per informazioni sulla creazione e sull'uso delle espressioni, vedere il [filtro TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).|
|**/?**|Visualizza informazioni sull'utilizzo.|
|**/Logger:[*uri/nome descrittivo*]**|Specifica un logger per i risultati dei test.<br />Esempio: per registrare i risultati in un file di Risultati test di Visual Studio (TRX), usare **/Logger:trx**.<br />Esempio: per pubblicare i risultati dei test in Team Foundation Server, usare TfsPublisher:<br />**/logger:TfsPublisher;**<br />**Collection=<project url\>;**<br />**BuildName=<nome build\>;**<br />**TeamProject=<project name\>;**<br />**[;Platform=<Il valore predefinito è "Qualsiasi CPU">]**<br />**[;Flavor=<Il valore predefinito è "Debug">]**<br />**[;RunTitle=<titolo\>]**|
|**/ListTests:[*nome file*]**|Elenca i test individuati dal contenitore di test specificato.|
|**/ListDiscoverers**|Elenca gli agenti di individuazione test installati.|
|**/ListExecutors**|Elenca gli executor di test installati.|
|**/ListLoggers**|Elenca i logger di test installati.|
|**/ListSettingsProviders**|Elenca i provider di impostazioni test installati.|
|**/Blame**|Monitora i test durante l'esecuzione e, se il processo host del test si arresta in modo anomalo, genera i nomi dei test nella sequenza di esecuzione fino al test specifico che era in esecuzione al momento dell'arresto anomalo. Questo output semplifica l'isolamento del test che causa l'errore e l'ulteriore diagnosi. [Altre informazioni](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag:[*nome file*]**|Scrive i log di traccia di diagnostica nel file specificato.|
|**/ResultsDirectory:[*percorso*]**|Directory dei risultati dei test che verrà creata nel percorso specificato, se non esistente.<br />Esempio: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*ID processo padre*]**|ID di processo del processo padre responsabile dell'avvio processo corrente.|
|**/Port:[*porta*]**|La porta per la connessione socket e la ricezione dei messaggi di evento.|
|**/Collect:[*nome descrittivo agente di raccolta dati*]**|Abilita l'agente di raccolta dati per l'esecuzione dei test. [Altre informazioni](https://aka.ms/vstest-collect).|

> [!TIP]
> Opzioni e valori non applicano la distinzione tra maiuscole e minuscole.

## <a name="examples"></a>Esempi

La sintassi per l'esecuzione di *VSTest.Console.exe* è:

`Vstest.console.exe [TestFileNames] [Options]`

Il comando riportato di seguito esegue *VSTest.Console.exe* per la libreria di test **myTestProject.dll**:

```cmd
vstest.console.exe myTestProject.dll
```

Il comando riportato di seguito esegue *VSTest.Console.exe* con più file di test. Per separare i nomi di file di test, usare gli spazi:

```cmd
Vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

Il comando riportato di seguito esegue *VSTest.Console.exe* con diverse opzioni. Esegue i test indicati nel file *myTestFile.dll* in un processo isolato e usa le impostazioni specificate nel file *Local.RunSettings*. Esegue inoltre solo i test contrassegnati "Priority=1" e registra i risultati in un file con estensione *trx*.

```cmd
vstest.console.exe  myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```
