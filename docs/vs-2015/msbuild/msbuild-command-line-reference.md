---
title: Riferimenti alla riga di comando di MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, msbuild.exe
- MSBuild, command line reference
- msbuild.exe
ms.assetid: edaa65ec-ab8a-42a1-84cb-d76d5b2f4584
caps.latest.revision: 61
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8d40bfefb1f89496b538612dfa1819cc6d65c76c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181061"
---
# <a name="msbuild-command-line-reference"></a>Riferimenti alla riga di comando di MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si usa MSBuild.exe per compilare un file di progetto o di soluzione, si possono includere varie opzioni per specificare diversi aspetti del processo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
MSBuild.exe [Switches] [ProjectFile]  
```  
  
## <a name="arguments"></a>Argomenti  
  
|Argomento|DESCRIZIONE|  
|--------------|-----------------|  
|`ProjectFile`|Compila le destinazioni nel file di progetto specificato. Se non si specifica un file di progetto, in MSBuild viene eseguita una ricerca nella directory di lavoro corrente di un nome file la cui estensione termina in "proj" e viene usato il file in questione. È inoltre possibile specificare un file di soluzione di Visual Studio per questo argomento.|  
  
## <a name="switches"></a>Opzioni  
  
|Opzione|Forma breve|DESCRIZIONE|  
|------------|----------------|-----------------|  
|/help|/? o /h|Visualizza le informazioni sull'utilizzo. Il comando seguente è un esempio:<br /><br /> `msbuild.exe /?`|  
|/detailedsummary|/ds|Mostra informazioni dettagliate alla fine del log di compilazione sulle configurazioni che sono state compilate e su come sono state pianificate nei nodi.|  
|/ignoreprojectextensions: `extensions`|/ignore: `extensions`|Ignora le estensioni specificate quando si devono individuare i file di progetto da compilare. Usare un punto e virgola o una virgola per separare più estensioni, come illustrato nel seguente esempio:<br /><br /> `/ignoreprojectextensions:.vcproj,.sln`|  
|/maxcpucount[:`number`]|/m[:`number`]|Specifica il numero massimo di processi simultanei da usare durante la compilazione. Se non si include questa opzione, il valore predefinito è 1. Se si include questa opzione senza specificare un valore, in MSBuild verranno usati fino al numero massimo di processori presenti nel computer. Per altre informazioni, vedere [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> Nell'esempio seguente viene indicato a MSBuild di eseguire la compilazione usando tre processi MSBuild, consentendo la compilazione contemporanea di tre progetti:<br /><br /> `msbuild myproject.proj /maxcpucount:3`|  
|/noautoresponse|/noautorsp|Non include automaticamente alcun file MSBuild.rsp.|  
|/nodeReuse:`value`|/nr:`value`|Abilita o disabilita il riutilizzo di nodi MSBuild. È possibile specificare i valori seguenti:<br /><br /> -   **True**. I nodi rimangono al termine della compilazione in modo da poter essere usati nelle compilazioni successive (impostazione predefinita).<br />-   **False**. I nodi non rimangono al termine della compilazione.<br /><br /> Un nodo corrisponde a un progetto che è in esecuzione. Se si include l'opzione **/maxcpucount**, più nodi possono essere eseguiti contemporaneamente.|  
|/nologo||Non visualizza l'intestazione di avvio né il messaggio di copyright.|  
|/preprocess[:`filepath`]|/pp[:`filepath`]|Crea un singolo file di progetto aggregato effettuando l'inlining di tutti i file che vengono importati durante una compilazione, contrassegnandone i limiti. È possibile usare questa opzione per determinare più facilmente quali file vengono importati, da dove i file vengono importati e quali file contribuiscono alla compilazione. Quando si usa questa opzione, il progetto non viene compilato.<br /><br /> Se si specifica un oggetto `filepath`, il file di progetto aggregato viene restituito come output al file. In caso contrario, l'output viene visualizzato nella finestra della console.<br /><br /> Per informazioni su come usare il `Import` elemento da inserire un file di progetto in un altro file di progetto, vedere [elemento Import (MSBuild)](../msbuild/import-element-msbuild.md) e [come: Usare la stessa destinazione in più file di progetto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).|  
|/property:`name`=`value`|/p:`name`=`value`|Imposta o esegue l'override delle proprietà specificate a livello di progetto, dove `name` è il nome della proprietà e `value` è il valore della proprietà. Specificare separatamente ogni proprietà o usare un punto e virgola o una virgola per separare più proprietà, come illustrato nel seguente esempio:<br /><br /> `/property:WarningLevel=2;OutDir=bin\Debug`|  
|/target:`targets`|/t:`targets`|Compila le destinazioni specificate nel progetto. Specificare separatamente ogni destinazione o usare un punto e virgola o una virgola per separare più destinazioni, come illustrato nel seguente esempio:<br /><br /> `/target:Resources;Compile`<br /><br /> Se si specificano tutte le destinazioni usando questa opzione, queste vengono eseguite al posto delle destinazioni nell'attributo `DefaultTargets` nel file di progetto. Per altre informazioni, vedere [ordine di compilazione delle destinazioni](../msbuild/target-build-order.md) e [come: Specificare quale destinazione compilare per prima](../msbuild/how-to-specify-which-target-to-build-first.md).<br /><br /> Una destinazione è un gruppo di attività. Per altre informazioni, vedere [Destinazioni](../msbuild/msbuild-targets.md).|  
|/toolsversion:`version`|/tv:`version`|Specifica la versione del set di strumenti da usare per compilare il progetto, come illustrato nel seguente esempio: `/toolsversion:3.5`<br /><br /> Usando questa opzione è possibile compilare un progetto e specificare una versione diversa dalla versione specificata in [Elemento Project (MSBuild)](../msbuild/project-element-msbuild.md). Per altre informazioni, vedere [Override delle impostazioni ToolsVersion](../msbuild/overriding-toolsversion-settings.md).<br /><br /> Per MSBuild 4.5, si possono specificare i seguenti valori per `version`: 2.0, 3.5 e 4.0. Se si specifica 4.0, la proprietà di compilazione `VisualStudioVersion` specifica i subset di strumenti da usare. Per altre informazioni, vedere la sezione relativa ai subset di strumenti in [Set di strumenti di MSBuild (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).<br /><br /> Un set di strumenti è costituito da attività, destinazioni e strumenti usati per compilare un'applicazione. Gli strumenti includono compilatori come csc.exe e vbc.exe. Per altre informazioni sui set di strumenti, vedere [Set di strumenti di MSBuild (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [Configurazioni standard e personalizzate del set di strumenti](../msbuild/standard-and-custom-toolset-configurations.md) e [Panoramica del multitargeting di MSBuild](../msbuild/msbuild-multitargeting-overview.md). **Nota:**  La versione del set di strumenti non è la stessa del framework di destinazione, vale a dire la versione di .NET Framework con cui è prevista l'esecuzione di un progetto. Per altre informazioni, vedere [Framework e piattaforma di destinazione di MSBuild](../msbuild/msbuild-target-framework-and-target-platform.md).|  
|/validate:[`schema`]|/val[`schema`]|Convalida il file di progetto e, se la convalida ha esito positivo, compila il progetto.<br /><br /> Se non si specifica `schema`, il progetto viene convalidato in base allo schema predefinito.<br /><br /> Se si specifica `schema`, il progetto viene convalidato in base allo schema specificato.<br /><br /> L'impostazione seguente è un esempio: `/validate:MyExtendedBuildSchema.xsd`|  
|/verbosity:`level`|/v:`level`|Specifica la quantità di informazioni da visualizzare nel log di compilazione. Ogni logger visualizza gli eventi in base al livello di dettaglio impostato per il logger.<br /><br /> È possibile specificare i seguenti livelli di dettaglio: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.<br /><br /> L'impostazione seguente è un esempio: `/verbosity:quiet`|  
|/version|/ver|Visualizza solo le informazioni sulla versione. Il progetto non viene compilato.|  
|@`file`||Inserisce le opzioni della riga di comando da un file di testo. Se si dispone di più file, devono essere specificati separatamente. Per altre informazioni, vedere [File di risposta MSBuild](../msbuild/msbuild-response-files.md).|  
  
### <a name="switches-for-loggers"></a>Opzioni per logger  
  
|Opzione|Forma breve|DESCRIZIONE|  
|------------|----------------|-----------------|  
|/consoleloggerparameters:<br /><br /> `parameters`|/clp:`parameters`|Passa i parametri specificati al logger di console tramite cui le informazioni sulla compilazione vengono visualizzate nella finestra della console. È possibile specificare i parametri riportati di seguito:<br /><br /> -   **PerformanceSummary**. Mostra il tempo necessario per attività, destinazioni e progetti.<br />-   **Summary**. Mostra il riepilogo di avvisi ed errori alla fine.<br />-   **NoSummary**. Non mostra il riepilogo di avvisi ed errori alla fine.<br />-   **ErrorsOnly**. Mostra solo gli errori.<br />-   **WarningsOnly**. Mostra solo gli avvisi.<br />-   **NoItemAndPropertyList**. Non mostra l'elenco degli elementi e delle proprietà che verrebbero visualizzati all'inizio di ogni compilazione del progetto se il livello di dettaglio fosse stato impostato su `diagnostic`.<br />-   **ShowCommandLine**. Mostra i messaggi `TaskCommandLineEvent`.<br />-   **ShowTimestamp**. Mostra il timestamp come prefisso di ogni messaggio.<br />-   **ShowEventId**. Mostra l'ID evento per ogni evento avviato, completato e per ogni messaggio.<br />-   **ForceNoAlign**. Non allinea il testo alla dimensione del buffer della console.<br />-   **DisableConsoleColor**. Usa i colori predefiniti della console per tutti i messaggi di registrazione.<br />-   **DisableMPLogging**. Disabilita lo stile di registrazione del multiprocessore dell'output quando è in esecuzione in modalità non multiprocessore.<br />-   **EnableMPLogging**. Abilita lo stile di registrazione del multiprocessore anche quando è in esecuzione in modalità non multiprocessore. Questo stile di registrazione è attivato per impostazione predefinita.<br />-   **Verbosity**. Esegue l'override dell'impostazione **/verbosity** per questo logger.<br /><br /> Usare un punto e virgola o una virgola per separare più parametri, come illustrato nell'esempio seguente:<br /><br /> `/consoleloggerparameters:PerformanceSummary;NoSummary /verbosity:minimal`|  
|/distributedFileLogger|/dfl|Registra l'output di compilazione di ogni nodo MSBuild nel relativo file. Il percorso iniziale per questi file è la directory attuale. Per impostazione predefinita, i file vengono denominati "MSBuild*NodeId*.log". È possibile usare l'opzione **/fileLoggerParameters** per specificare la posizione dei file e di altri parametri per fileLogger.<br /><br /> Se un file di log viene denominato usando l'opzione **/fileLoggerParameters**, nel logger distribuito questo nome verrà usato come modello e l'ID del nodo verrà aggiunto a questo nome durante la creazione di un file di log per ogni nodo.|  
|/distributedlogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|/dl:`central logger`*`forwarding logger`|Registra gli eventi di MSBuild, associando un'istanza di logger diversa a ogni nodo. Per specificare più logger, specificare ciascun logger separatamente.<br /><br /> Usare la sintassi del logger per specificare un logger. Per la sintassi del logger, vedere l'opzione **/logger** riportata di seguito.<br /><br /> Negli esempi seguenti viene illustrato l'utilizzo di questa opzione:<br /><br /> `/dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|  
|/fileLogger<br /><br /> *[number]*|/fl[`number`]|Registra l'output di compilazione in un singolo file nella directory corrente. Se non si specifica `number`, il file di output viene denominato msbuild.log. Se si specifica `number`, il file di output viene denominato msbuild`n`.log, dove n è `number`. `Number` può essere una cifra compresa tra 1 e 9.<br /><br /> È possibile usare l'opzione **/fileLoggerParameters** per specificare la posizione dei file e di altri parametri per fileLogger.|  
|/fileloggerparameters:[number]<br /><br /> `parameters`|/flp:[ `number`] `parameters`|Specifica parametri aggiuntivi per il logger di file e il logger di file distribuito. La presenza di questa opzione implica che sia presente l'opzione /**filelogger[** `number` **]** corrispondente. `Number` può essere una cifra compresa tra 1 e 9.<br /><br /> Si possono usare tutti i parametri elencati per **/consoleloggerparameters**. È inoltre possibile usare uno o più dei seguenti parametri:<br /><br /> -   **LogFile**. Percorso del file di log nel quale viene scritto il log di compilazione. Questo percorso viene aggiunto come prefisso ai nomi dei file di log tramite il logger di file distribuito.<br />-   **Append**. Determina se il log di compilazione viene aggiunto al file di log o se lo sovrascrive. Quando si imposta l'opzione, il log di compilazione viene aggiunto al file di log. in caso contrario, il contenuto di un file di log esistente viene sovrascritto.<br />     Se si include l'opzione Append, il log viene aggiunto indipendentemente dall'impostazione su true o false. Se non si include l'opzione Append, il log viene sovrascritto.<br />     In questo caso il file viene sovrascritto: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log`<br />     In questo caso il file viene aggiunto: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=true`<br />     In questo caso il file viene aggiunto: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=false`<br />-   **Encoding**. Specifica la codifica del file (ad esempio UTF-8, Unicode o ASCII).<br /><br /> Nell'esempio seguente vengono generati file di log differenti per gli avvisi e gli errori:<br /><br /> `/flp1:logfile=errors.txt;errorsonly /flp2:logfile=warnings.txt;warningsonly`<br /><br /> Negli esempi seguenti vengono illustrate altre possibilità:<br /><br /> `/fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `/flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `/flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `/flp2:errorsonly;logfile=msbuild.err`|  
|/logger:<br /><br /> `logger`|/l:`logger`|Specifica il logger da usare per registrare eventi da MSBuild. Per specificare più logger, specificare ciascun logger separatamente.<br /><br /> Usare la sintassi seguente per `logger`: `[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> Usare la sintassi seguente per `LoggerClass`: `[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Non è necessario specificare la classe logger se nell'assembly è contenuto esattamente un logger.<br /><br /> Usare la sintassi seguente per `LoggerAssembly`: `{``AssemblyName``[,``StrongName``] &#124;` `AssemblyFile``}`<br /><br /> I parametri del logger sono facoltativi e vengono passati al logger esattamente come vengono inseriti.<br /><br /> Negli esempi seguenti viene usata l'opzione **/logger**.<br /><br /> `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|  
|/noconsolelogger|/noconlog|Disabilita il logger della console predefinito e non registra gli eventi nella console.|  
  
## <a name="example"></a>Esempio  
 L'esempio seguente compila la destinazione `rebuild` del progetto `MyProject.proj`.  
  
```  
MSBuild.exe MyProject.proj /t:rebuild  
```  
  
## <a name="example"></a>Esempio  
 È possibile usare MSBuild.exe per eseguire compilazioni più complesse. Ad esempio, è possibile compilare destinazioni specifiche di progetti specifici in una soluzione. Nell'esempio seguente viene ricompilato il progetto `NotInSolutionFolder` e pulito il progetto `InSolutionFolder` che si trova nella cartella della soluzione `NewFolder`.  
  
```  
msbuild SlnFolders.sln /t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Proprietà di progetto MSBuild comuni](../msbuild/common-msbuild-project-properties.md)
