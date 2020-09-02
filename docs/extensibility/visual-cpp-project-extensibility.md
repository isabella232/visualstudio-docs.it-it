---
title: Estendibilità del progetto Visual C++
ms.date: 04/23/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10869ad290b0b8df614d25d792d0b3ed1e88eb17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825559"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Estendibilità del sistema di progetto C++ di Visual Studio e integrazione del set di strumenti

Il sistema di progetto Visual C++ viene utilizzato per i file. vcxproj. Si basa su [CPS (Common Project System) di Visual Studio](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) e fornisce punti di estendibilità specifici di C++ aggiuntivi per semplificare l'integrazione dei nuovi set di strumenti, le architetture di compilazione e le piattaforme di destinazione.

## <a name="c-msbuild-targets-structure"></a>Struttura di destinazioni MSBuild C++

Tutti i file con estensione vcxproj importano questi file:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Questi file definiscono poco. Ma importano altri file in base a questi valori di proprietà:

- `$(ApplicationType)`

   Esempi: Windows Store, Android, Linux

- `$(ApplicationTypeRevision)`

   Deve essere una stringa di versione valida nel formato Major. minor [. Build [. Revision]].

   Esempi: 1,0, 10.0.0.0

- `$(Platform)`

   Architettura di compilazione, denominata "Platform" per motivi cronologici.

   Esempi: Win32, x86, x64, ARM

- `$(PlatformToolset)`

   Esempi: V140, V141, v141_xp, LLVM

Questi valori di proprietà specificano i nomi delle cartelle nella `$(VCTargetsPath)` cartella radice:

> `$(VCTargetsPath)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;*Tipo di applicazione*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Piattaforme*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)` \
&nbsp;&nbsp;&nbsp;&nbsp;*Piattaforme*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`

La `$(VCTargetsPath)` \\ cartella *Platforms* \\ viene utilizzata quando `$(ApplicationType)` è vuoto per i progetti desktop di Windows.

### <a name="add-a-new-platform-toolset"></a>Aggiungere un nuovo set di strumenti della piattaforma

Per aggiungere un nuovo set di strumenti, ad esempio "set di strumenti" per la piattaforma Win32 esistente, creare una cartella del set di *strumenti* in `$(VCTargetsPath)` * \\ piattaforme \\ Win32 \\ \\ PlatformToolsets*e creare i file *Toolset. props* e *Toolset. targets* .

Ogni nome di cartella in *PlatformToolsets* viene visualizzato nella finestra di dialogo **Proprietà progetto** come **set di strumenti della piattaforma** disponibile per la piattaforma specificata, come illustrato di seguito:

![Proprietà del set di strumenti della piattaforma nella finestra di dialogo Pagine delle proprietà del progetto](media/vc-project-extensibility-platform-toolset-property.png "Proprietà del set di strumenti della piattaforma nella finestra di dialogo Pagine delle proprietà del progetto")

Creare cartelle di set di *strumenti* e *set di strumenti. props* e Toolset. *targets* simili in ogni cartella della piattaforma esistente supportata da questo set di strumenti.

### <a name="add-a-new-platform"></a>Aggiungi una nuova piattaforma

Per aggiungere una nuova piattaforma, ad esempio "piattaforma", creare una cartella di *piattaforma* con `$(VCTargetsPath)` * \\ piattaforme \\ *e creare file Platform. *default. props*, *Platform. props*e *Platform. targets* al suo interno. Creare anche una `$(VCTargetsPath)` cartella * \\ Platforms \\ *<strong><em>MyPlatform</em></strong>* \\ PlatformToolsets \\ * e creare almeno un set di strumenti.

Tutti i nomi di cartella nella cartella *Platforms* per ogni `$(ApplicationType)` e `$(ApplicationTypeRevision)` vengono visualizzati nell'IDE come opzioni di **piattaforma** disponibili per un progetto.

![Nuova opzione della piattaforma nella finestra di dialogo nuova piattaforma progetto](media/vc-project-extensibility-new-project-platform.png "Nuova opzione della piattaforma nella finestra di dialogo nuova piattaforma progetto")

### <a name="add-a-new-application-type"></a>Aggiungere un nuovo tipo di applicazione

Per aggiungere un nuovo tipo di applicazione, creare una cartella *MyApplicationType* in `$(VCTargetsPath)` * \\ tipo \\ di applicazione* e creare un file *defaults. props* al suo interno. Almeno una revisione è necessaria per un tipo di applicazione, quindi creare anche un `$(VCTargetsPath)` * \\ tipo di applicazione \\ MyApplicationType \\ 1,0* cartella e creare un file *defaults. props* al suo interno. È anche necessario creare una `$(VCTargetsPath)` cartella * \\ ApplicationType \\ MyApplicationType \\ 1,0 \\ Platforms* e creare almeno una piattaforma.

`$(ApplicationType)``$(ApplicationTypeRevision)`le proprietà e non sono visibili nell'interfaccia utente. Sono definiti nei modelli di progetto e non possono essere modificati dopo la creazione del progetto.

## <a name="the-vcxproj-import-tree"></a>Albero di importazione. vcxproj

Un albero semplificato delle importazioni per i file di destinazioni e destinazioni di Microsoft C++ è simile al seguente:

> `$(VCTargetsPath)`\\*Microsoft. cpp. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore* \\ *Impostazione predefinita* \\ \* . *oggetti prop* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Application Type* \\ Tipo `$(ApplicationType)` di \\ applicazione *Default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Application Type* \\ Tipo `$(ApplicationType)` \\ di `$(ApplicationTypeRevision)` applicazione \\ *Default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Application Type* \\ Tipo `$(ApplicationType)` \\ di `$(ApplicationTypeRevision)` applicazione \\ *Platforms* \\ `$(Platform)` Piattaforme \\ *Platform. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\ *Impostazione predefinita* \\ \* . *oggetti prop*

I progetti desktop di Windows non definiscono `$(ApplicationType)` , quindi importano solo

> `$(VCTargetsPath)`\\*Microsoft. cpp. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore* \\ *Impostazione predefinita* \\ \* . *oggetti prop* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Platforms* \\ `$(Platform)` Piattaforme \\ *Platform. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\ *Impostazione predefinita* \\ \* . *oggetti prop*

Verrà usata la `$(_PlatformFolder)` proprietà per mantenere i `$(Platform)` percorsi della cartella della piattaforma. Questa proprietà è

> `$(VCTargetsPath)`\\*Piattaforme*\\`$(Platform)`

per le app desktop di Windows e

> `$(VCTargetsPath)`\\*Application Type* \\ Tipo `$(ApplicationType)` \\ di `$(ApplicationTypeRevision)` applicazione \\ *Piattaforme*\\`$(Platform)`

per tutti gli altri elementi.

I file di Props vengono importati nell'ordine seguente:

> `$(VCTargetsPath)`\\*Microsoft. cpp. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Platform. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore* \\ \* . *oggetti prop* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets* \\ `$(PlatformToolset)` PlatformToolsets \\ *Set di strumenti. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* . *oggetti prop*

I file di destinazione vengono importati nell'ordine seguente:

> `$(VCTargetsPath)`\\*Microsoft. cpp. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Current. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore* \\ \* . *destinazioni* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets* \\ `$(PlatformToolset)` PlatformToolsets \\ *Set di strumenti. target* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* . *destinazioni*

Se è necessario definire alcune proprietà predefinite per il set di strumenti, è possibile aggiungere file alle cartelle ImportBefore e ImportAfter appropriate.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Creare file di set di strumenti. props e Toolset. targets

I file *Toolset. props* e *Toolset. targets* hanno il controllo completo su ciò che accade durante una compilazione quando viene usato questo set di strumenti. Possono inoltre controllare i debugger disponibili, parte dell'interfaccia utente dell'IDE, ad esempio il contenuto nella finestra di dialogo **pagine delle proprietà** e altri aspetti del comportamento del progetto.

Sebbene un set di strumenti possa eseguire l'override dell'intero processo di compilazione, in genere si vuole che il set di strumenti modifichi o aggiunga solo alcuni passaggi di compilazione oppure per usare diversi strumenti di compilazione, come parte di un processo di compilazione esistente. Per portare a termine questo obiettivo, è possibile importare un set di strumenti e i file di destinazioni comuni. A seconda di ciò che si vuole eseguire nel set di strumenti, questi file possono essere utili per l'uso come importazioni o come esempi:

- `$(VCTargetsPath)`\\*Microsoft. CppCommon. targets*

  Questo file definisce le parti principali del processo di compilazione nativo e importa anche:

  - `$(VCTargetsPath)`\\*Microsoft. CppBuild. targets*

  - `$(VCTargetsPath)`\\*Microsoft. BuildSteps. targets*

  - `$(MSBuildToolsPath)`\\*Microsoft. Common. targets*

- `$(VCTargetsPath)`\\*Microsoft. cpp. Common. props*

   Imposta le impostazioni predefinite per i set di strumenti che usano i compilatori Microsoft e le finestre di destinazione.

- `$(VCTargetsPath)`\\*Microsoft. cpp. WindowsSDK. props*

   Questo file determina la posizione del Windows SDK e definisce alcune proprietà importanti per le app destinate a Windows.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Integrare destinazioni specifiche del set di strumenti con il processo di compilazione C++ predefinito

Il processo di compilazione C++ predefinito è definito in *Microsoft. CppCommon. targets*. Le destinazioni non chiamano strumenti di compilazione specifici; specificano i passaggi di compilazione principali, l'ordine e le dipendenze.

La compilazione C++ prevede tre passaggi principali, rappresentati dalle destinazioni seguenti:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Poiché ogni passaggio di compilazione può essere eseguito in modo indipendente, le destinazioni eseguite in un passaggio non possono basarsi sui gruppi di elementi e sulle proprietà definiti nelle destinazioni eseguite come parte di un passaggio diverso. Questa divisione consente alcune ottimizzazioni delle prestazioni di compilazione. Sebbene non venga usato per impostazione predefinita, è comunque consigliabile rispettare la separazione.

Le destinazioni eseguite all'interno di ogni passaggio sono controllate da queste proprietà:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Ogni passaggio ha anche le proprietà before e After.

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

Per esempi delle destinazioni incluse in ogni passaggio, vedere il file *Microsoft. CppBuild. targets* :

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Se si osservano le destinazioni, ad esempio `_ClCompile` , si noterà che non eseguono alcuna operazione direttamente da soli, ma dipendono invece da altre destinazioni, tra cui `ClCompile` :

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` e altre destinazioni specifiche dello strumento di compilazione sono definite come destinazioni vuote in *Microsoft. CppBuild. targets*:

```xml
<Target Name="ClCompile"/>
```

Poiché la `ClCompile` destinazione è vuota, a meno che non venga sottoposta a override da un set di strumenti, non viene eseguita alcuna azione di compilazione reale. Le destinazioni del set di strumenti possono eseguire l'override della `ClCompile` destinazione, ovvero possono contenere un'altra `ClCompile` definizione dopo l'importazione di *Microsoft. CppBuild. targets*:

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Nonostante il nome, creato prima dell'implementazione del supporto multipiattaforma da parte di Visual Studio, `ClCompile` non è necessario che la destinazione chiami CL.exe. Può anche chiamare Clang, gcc o altri compilatori utilizzando le attività MSBuild appropriate.

La `ClCompile` destinazione non deve avere alcuna dipendenza ad eccezione della `SelectClCompile` destinazione, che è necessaria per il funzionamento del singolo comando di compilazione file nell'IDE.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>Attività di MSBuild da usare nelle destinazioni del set di strumenti

Per richiamare uno strumento di compilazione effettivo, è necessario che la destinazione chiami un'attività MSBuild. È disponibile un' [attività Exec](../msbuild/exec-task.md) di base che consente di specificare una riga di comando per l'esecuzione. Tuttavia, gli strumenti di compilazione hanno in genere molte opzioni, input. e output per tenere traccia delle compilazioni incrementali, quindi è più sensato avere attività speciali. Ad esempio, l' `CL` attività converte le proprietà MSBuild in CL.exe opzioni, le scrive in un file di risposta e chiama CL.exe. Tiene inoltre traccia di tutti i file di input e di output per le successive compilazioni incrementali. Per altre informazioni, vedere [compilazioni incrementali e controlli aggiornati](#incremental-builds-and-up-to-date-checks).

Il Microsoft.Cpp.Common.Tasks.dll implementa queste attività:

- `BSCMake`

- `CL`

- `ClangCompile` (commutatori Clang-GCC)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (ad esempio exec ma con rilevamento di input e output)

- `SetEnv`

- `GetOutOfDateItems`

Se si dispone di uno strumento che esegue la stessa azione di uno strumento esistente e che dispone di opzioni della riga di comando simili (come Clang-CL e CL do), è possibile utilizzare la stessa attività per entrambe.

Se è necessario creare una nuova attività per uno strumento di compilazione, è possibile scegliere tra le opzioni seguenti:

1. Se si usa questa attività raramente o se alcuni secondi non sono importanti per la compilazione, è possibile usare le attività' inline ' di MSBuild:

   - Attività XAML (regola di compilazione personalizzata)

     Per un esempio di dichiarazione di attività XAML, vedere `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.xml*e per il relativo utilizzo, vedere `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *MASM. targets*.

   - [Attività Code](../msbuild/msbuild-inline-tasks.md)

1. Se si desidera migliorare le prestazioni delle attività o solo le funzionalità più complesse, utilizzare il normale processo di [scrittura dell'attività](../msbuild/task-writing.md) MSBuild.

   Se non tutti gli input e gli output dello strumento sono elencati nella riga di comando dello strumento, come `CL` nei `MIDL` case, e e `RC` se si desidera che il rilevamento automatico dei file di input e di output e la creazione di file con estensione TLog, derivare l'attività dalla `Microsoft.Build.CPPTasks.TrackedVCToolTask` classe. Attualmente, sebbene sia presente la documentazione per la classe di base [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) , non sono disponibili esempi o documentazione per i dettagli della `TrackedVCToolTask` classe. Se si tratta di un interesse particolare, aggiungere la voce a una richiesta in [developercommunity.VisualStudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="incremental-builds-and-up-to-date-checks"></a>Compilazioni incrementali e controlli aggiornati

Le destinazioni di compilazione incrementale di MSBuild predefinite usano `Inputs` `Outputs` gli attributi e. Se vengono specificati, MSBuild chiama la destinazione solo se uno degli input ha un timestamp più recente rispetto a tutti gli output. Poiché i file di origine spesso includono o importano altri file e gli strumenti di compilazione generano output diversi a seconda delle opzioni dello strumento, è difficile specificare tutti gli input e gli output possibili nelle destinazioni MSBuild.

Per gestire questo problema, la compilazione C++ usa una tecnica diversa per supportare le compilazioni incrementali. La maggior parte delle destinazioni non specifica gli input e gli output e, di conseguenza, viene sempre eseguita durante la compilazione. Le attività chiamate da destinazioni scrivono informazioni su tutti gli input e gli output in file *tlog* con estensione tlog. I file con estensione TLog vengono usati da compilazioni successive per verificare cosa è stato modificato e devono essere ricompilati e quali sono gli elementi aggiornati. I file con estensione tlog sono anche l'unica fonte per il controllo predefinito di compilazione aggiornato nell'IDE.

Per determinare tutti gli input e gli output, le attività native degli strumenti utilizzano tracker.exe e la classe [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) fornita da MSBuild.

Microsoft.Build.CPPTasks.Common.dll definisce la `TrackedVCToolTask` classe di base astratta pubblica. La maggior parte delle attività native degli strumenti sono derivate da questa classe.

A partire da Visual Studio 2017 Update 15,8, è possibile usare l' `GetOutOfDateItems` attività implementata in Microsoft.Cpp.Common.Tasks.dll per produrre file con estensione tlog per destinazioni personalizzate con input e output noti.
In alternativa, è possibile crearli usando l' `WriteLinesToFile` attività. Vedere la `_WriteMasmTlogs` destinazione in `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *MASM. targets* come esempio.

## <a name="tlog-files"></a>file con estensione TLog

Sono disponibili tre tipi di file con estensione tlog: *lettura*, *scrittura*e *riga di comando*. I file con estensione tlog di lettura e scrittura vengono usati dalle compilazioni incrementali e dalla verifica aggiornata nell'IDE. I file con estensione tlog della riga di comando vengono usati solo nelle compilazioni incrementali.

MSBuild fornisce queste classi helper per la lettura e la scrittura dei file con estensione tlog:

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

La classe [FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) può essere usata per accedere ai file con estensione tlog di lettura e scrittura e per identificare gli input più recenti degli output o se manca un output. Viene usato nel controllo aggiornato.

I file con estensione tlog della riga di comando contengono informazioni sulle righe di comando usate nella compilazione. Vengono usati solo per le compilazioni incrementali, non per i controlli aggiornati, quindi il formato interno è determinato dall'attività MSBuild che li produce.

### <a name="read-tlog-format"></a>Formato Read. tlog

*Legge* i file. tlog ( \* . Read. \* . tlog) contiene informazioni sui file di origine e le relative dipendenze.

Un accento circonflesso ( **^** ) all'inizio di una riga indica una o più origini. Le origini che condividono le stesse dipendenze sono separate da una barra verticale ( **\|** ).

I file di dipendenza sono elencati dopo le origini, ognuno su una riga a parte. Tutti i nomi di file sono percorsi completi.

Si supponga, ad esempio, che le origini del progetto si trovino in *F: \\ test \\ ConsoleApplication1 \\ ConsoleApplication1*. Se il file di origine, *Class1. cpp*, include,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

il file *CL. Read. 1. tlog* contiene il file di origine seguito dalle due dipendenze:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Non è necessario scrivere nomi di file in lettere maiuscole, ma si tratta di una praticità per alcuni strumenti.

### <a name="write-tlog-format"></a>Formato Write. tlog

*Write* . tlog ( \* . Write. \* . tlog) i file connettono origini e output.

Un accento circonflesso ( **^** ) all'inizio di una riga indica una o più origini. Più origini sono separate da una barra verticale ( **\|** ).

I file di output compilati dalle origini devono essere elencati dopo le origini, ognuno su una riga a parte. Tutti i nomi di file devono essere percorsi completi.

Ad esempio, per un semplice progetto ConsoleApplication con un file di origine aggiuntivo *Class1. cpp*, il file *link. Write. 1. tlog* può contenere:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Compilazione in fase di progettazione

Nell'IDE i progetti. vcxproj utilizzano un set di destinazioni MSBuild per ottenere informazioni aggiuntive dal progetto e per rigenerare i file di output. Alcune di queste destinazioni vengono usate solo nelle compilazioni in fase di progettazione, ma molte di esse vengono usate sia nelle compilazioni regolari che nelle compilazioni in fase di progettazione.

Per informazioni generali sulle compilazioni in fase di progettazione, vedere la documentazione di CPS per le [compilazioni in fase di progettazione](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Questa documentazione è applicabile solo in parte ai progetti Visual C++.

Le `CompileDesignTime` `Compile` destinazioni e indicate nella documentazione relativa alle compilazioni in fase di progettazione non vengono mai eseguite per i progetti. vcxproj. I progetti Visual C++. vcxproj utilizzano destinazioni della fase di progettazione diverse per ottenere informazioni IntelliSense.

### <a name="design-time-targets-for-intellisense-information"></a>Destinazioni della fase di progettazione per le informazioni di IntelliSense

Le destinazioni in fase di progettazione usate nei progetti. vcxproj sono definite in `$(VCTargetsPath)` \\ *Microsoft. cpp. DesignTime. targets*.

La `GetClCommandLines` destinazione raccoglie le opzioni del compilatore per IntelliSense:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` : destinazioni solo in fase di progettazione, necessarie per l'inizializzazione della compilazione in fase di progettazione. Tra le altre cose, queste destinazioni disabilitano alcune delle normali funzionalità di compilazione per migliorare le prestazioni.

- `ComputeCompileInputsTargets` : set di destinazioni che modifica le opzioni e gli elementi del compilatore. Queste destinazioni vengono eseguite sia in fase di progettazione che in compilazioni regolari.

La destinazione chiama l' `CLCommandLine` attività per creare la riga di comando da utilizzare per IntelliSense. Anche in questo caso, nonostante il nome, può gestire non solo le opzioni CL, ma anche le opzioni Clang e GCC. Il tipo delle opzioni del compilatore è controllato dalla `ClangMode` Proprietà.

Attualmente, la riga di comando prodotta dall' `CLCommandLine` attività USA sempre i commutatori CL (anche in modalità Clang) perché sono più semplici da analizzare nel motore di IntelliSense.

Se si aggiunge una destinazione che viene eseguita prima della compilazione, sia normale che in fase di progettazione, assicurarsi che non interrompa le compilazioni in fase di progettazione o influisca sulle prestazioni. Il modo più semplice per testare la destinazione consiste nell'aprire un prompt dei comandi per gli sviluppatori ed eseguire il comando seguente:

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

Questo comando genera un log di compilazione dettagliato, *MSBuild. log*, che include un riepilogo delle prestazioni per le destinazioni e le attività alla fine.

Assicurarsi di usare `Condition ="'$(DesignTimeBuild)' != 'true'"` in tutte le operazioni che hanno senso solo per le compilazioni normali e non per le compilazioni in fase di progettazione.

### <a name="design-time-targets-that-generate-sources"></a>Destinazioni della fase di progettazione che generano origini

*Questa funzionalità è disabilitata per impostazione predefinita per i progetti desktop nativi e non è attualmente supportata nei progetti memorizzati nella cache*.

Se `GeneratorTarget` per un elemento di progetto sono definiti metadati, la destinazione viene eseguita automaticamente quando il progetto viene caricato e quando viene modificato il file di origine.

::: moniker range="vs-2017"

Ad esempio, per generare automaticamente file con estensione cpp o h da file XAML, i file Microsoft `$(VSInstallDir)` \\ *MSBuild* \\ *Microsoft* \\ *WindowsXaml* \\ *v15.0* \\ \* \\ *. Windows. UI. XAML. cpp. targets* di MSBuild definiscono le entità seguenti:

::: moniker-end

::: moniker range=">=vs-2019"

Ad esempio, per generare automaticamente file con estensione cpp o h da file XAML, i file Microsoft `$(VSInstallDir)` \\ *MSBuild* \\ *Microsoft* \\ *WindowsXaml* \\ *v16.0* \\ \* \\ *. Windows. UI. XAML. cpp. targets* di MSBuild definiscono le entità seguenti:

::: moniker-end

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

Per usare `Task.HostObject` per ottenere il contenuto non salvato dei file di origine, le destinazioni e le attività devono essere registrate come [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) per i progetti specificati in un pkgdef:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual C++ estensibilità del progetto nell'IDE di Visual Studio

Il sistema di progetto Visual C++ è basato sul [sistema del progetto di Visual](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)studio e usa i punti di estendibilità. Tuttavia, l'implementazione della gerarchia del progetto è specifica di Visual C++ e non basata su CPS, quindi l'estendibilità della gerarchia è limitata agli elementi del progetto.

### <a name="project-property-pages"></a>Pagina delle proprietà del progetto

Per informazioni generali sulla progettazione, vedere [la pagina relativa al multitargeting del Framework per progetti VC + +](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/).

In termini semplici, le pagine delle proprietà visualizzate nella finestra di dialogo delle **proprietà del progetto** per un progetto C++ vengono definite in base ai file delle *regole* . Un file di regole specifica un set di proprietà da visualizzare in una pagina delle proprietà e la modalità e la posizione in cui devono essere salvate nel file di progetto. I file delle regole sono file con estensione XML che usano il formato XAML. I tipi utilizzati per serializzarli sono descritti in [Microsoft. Build. Framework. XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes). Per ulteriori informazioni sull'utilizzo dei file delle regole nei progetti, vedere [file delle regole XML della pagina delle proprietà](/cpp/build/reference/property-page-xml-files).

È necessario aggiungere i file delle regole al `PropertyPageSchema` gruppo di elementi:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` i metadati limitano la visibilità della regola, che è controllata anche dal tipo di regola e può avere uno dei valori seguenti:

`Project` | `File` | `PropertySheet`

CPS supporta altri valori per il tipo di contesto, ma non vengono utilizzati nei progetti Visual C++.

Se la regola deve essere visibile in più di un contesto, usare i punti e virgola (**;**) per separare i valori di contesto, come illustrato di seguito:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Formato regola e tipi principali

Il formato della regola è semplice, quindi questa sezione descrive solo gli attributi che influiscono sulla modalità di ricerca della regola nell'interfaccia utente.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

L' `PageTemplate` attributo definisce il modo in cui la regola viene visualizzata nella finestra di dialogo **pagine delle proprietà** . L'attributo può avere uno dei valori seguenti:

| Attributo | Descrizione |
|------------| - |
| `generic` | Tutte le proprietà vengono visualizzate in una pagina in intestazioni di categoria<br/>La regola può essere visibile per `Project` i `PropertySheet` contesti e, ma non `File` .<br/><br/> Esempio: `$(VCTargetsPath)` \\ *1033* \\ *general.xml* |
| `tool` | Le categorie vengono visualizzate come sottopagine.<br/>La regola può essere visibile in tutti i contesti: `Project` , `PropertySheet` e `File` .<br/>La regola è visibile nelle proprietà del progetto solo se il progetto include elementi con `ItemType` definito in `Rule.DataSource` , a meno che il nome della regola non sia incluso nel `ProjectTools` gruppo di elementi.<br/><br/>Esempio: `$(VCTargetsPath)` \\ *1033* \\ *clang.xml* |
| `debugger` | La pagina viene visualizzata come parte della pagina di debug.<br/>Le categorie sono attualmente ignorate.<br/>Il nome della regola deve corrispondere all'attributo dell'oggetto MEF dell'utilità di avvio del debug `ExportDebugger` .<br/><br/>Esempio: `$(VCTargetsPath)` \\ *1033* \\ * \_ \_windows.xmllocale del debugger* |
| *personalizzato* | Modello personalizzato. Il nome del modello deve corrispondere all' `ExportPropertyPageUIFactoryProvider` attributo dell' `PropertyPageUIFactoryProvider` oggetto MEF. Vedere **Microsoft. VisualStudio. ProjectSystem. designers. Properties. IPropertyPageUIFactoryProvider**.<br/><br/> Esempio: `$(VCTargetsPath)` \\ *1033* \\ *userMacros.xml* |

Se la regola utilizza uno dei modelli basati su griglia delle proprietà, può utilizzare questi punti di estendibilità per le relative proprietà:

- [Editor di valori di proprietà](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Provider di valori enum dinamici](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Estendi una regola

Se si vuole usare una regola esistente, ma è necessario aggiungere o rimuovere, ovvero nascondere, solo alcune proprietà, è possibile creare una [regola di estensione](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Eseguire l'override di una regola

Forse si vuole che il set di strumenti usi la maggior parte delle regole predefinite del progetto, ma per sostituire solo una o alcune di esse. Si immagini, ad esempio, di voler solo modificare la regola C/C++ in modo da visualizzare diverse opzioni del compilatore. È possibile specificare una nuova regola con lo stesso nome e lo stesso nome visualizzato della regola esistente e includerla nel `PropertyPageSchema` gruppo di elementi dopo l'importazione delle destinazioni cpp predefinite. Nel progetto viene utilizzata solo una regola con un determinato nome e l'ultima inclusa nel `PropertyPageSchema` gruppo di elementi prevale.

#### <a name="project-items"></a>Elementi di progetto

Il file di *ProjectItemsSchema.xml* definisce `ContentType` i `ItemType` valori e per gli elementi trattati come elementi del progetto e definisce `FileExtension` gli elementi per determinare il gruppo di elementi a cui viene aggiunto un nuovo file.

Il file ProjectItemsSchema predefinito si trova in `$(VCTargetsPath)` \\ *1033* \\ *ProjectItemsSchema.xml*. Per estenderlo, è necessario creare un file di schema con un nuovo nome, ad esempio *MyProjectItemsSchema.xml*:

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

Quindi, nel file targets aggiungere:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Esempio: `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.xml*

### <a name="debuggers"></a>Debugger

Il servizio di debug in Visual Studio supporta l'estendibilità per il motore di debug. Per ulteriori informazioni, vedere gli esempi seguenti:

- [MIEngine, progetto open source che supporta il debug LLDB](https://github.com/Microsoft/MIEngine)

- [Esempio di motore di debug di Visual Studio](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Per specificare i motori di debug e altre proprietà per la sessione di debug, è necessario implementare un componente MEF dell' [utilità di avvio del debug](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) e aggiungere una `debugger` regola. Per un esempio, vedere il `$(VCTargetsPath)` \\ \\ file di \_windows.xml locale del debugger 1033 \_ .

### <a name="deploy"></a>Distribuire

i progetti. vcxproj usano l'estendibilità del sistema di progetto di Visual Studio per i [provider di distribuzione](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Verifica della compilazione aggiornata

Per impostazione predefinita, il controllo della build aggiornata richiede che i file Read. tlog e Write. tlog vengano creati nella `$(TlogLocation)` cartella durante la compilazione per tutti gli input e gli output di compilazione.

Per utilizzare un controllo di aggiornamento personalizzato:

1. Disabilitare il controllo di aggiornamento predefinito aggiungendo la `NoVCDefaultBuildUpToDateCheckProvider` funzionalità nel file *Toolset. targets* :

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Implementare il proprio [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Aggiornamento progetto

### <a name="default-vcxproj-project-upgrader"></a>Aggiornamento del progetto default. vcxproj

L'aggiornamento del progetto default. vcxproj modifica la `PlatformToolset` `ApplicationTypeRevision` versione del set di strumenti,, MSBuild e .NET Framework. Gli ultimi due vengono sempre modificati in base ai valori predefiniti della versione di Visual Studio, ma `PlatformToolset` `ApplicationTypeRevision` possono essere controllati da proprietà speciali di MSBuild.

Il programma di aggiornamento utilizza questi criteri per decidere se un progetto può essere aggiornato o meno:

1. Per i progetti che definiscono `ApplicationType` e `ApplicationTypeRevision` , esiste una cartella con un numero di revisione superiore rispetto a quello corrente.

1. La proprietà `_UpgradePlatformToolsetFor_<safe_toolset_name>` è definita per il set di strumenti corrente e il relativo valore non è uguale al set di strumenti corrente.

   In questi nomi di proprietà, *\<safe_toolset_name>* rappresenta il nome del set di strumenti con tutti i caratteri non alfanumerici sostituiti da un carattere di sottolineatura ( **\_** ).

Quando un progetto può essere aggiornato, partecipa al reindirizzamento della *soluzione*. Per ulteriori informazioni, vedere [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Se si desidera decorare i nomi di progetto in **Esplora soluzioni** quando i progetti utilizzano un set di strumenti specifico, definire una `_PlatformToolsetShortNameFor_<safe_toolset_name>` Proprietà.

Per esempi di `_UpgradePlatformToolsetFor_<safe_toolset_name>` `_PlatformToolsetShortNameFor_<safe_toolset_name>` definizioni di proprietà e, vedere il file *Microsoft. cpp. default. props* . Per esempi di utilizzo, vedere il `$(VCTargetPath)` \\ file *Microsoft. cpp. Platform. targets* .

### <a name="custom-project-upgrader"></a>Aggiornamento progetto personalizzato

Per usare un oggetto di aggiornamento del progetto personalizzato, implementare un componente MEF, come illustrato di seguito:

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

Il codice può importare e chiamare l'oggetto di aggiornamento predefinito. vcxproj:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` è definito in *Microsoft.VisualStudio.ProjectSystem.VS.dll* ed è simile a `IVsRetargetProjectAsync` .

Definire la `VCProjectUpgraderObjectName` proprietà per indicare al sistema del progetto di utilizzare l'oggetto di aggiornamento personalizzato:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Disabilita aggiornamento progetto

Per disabilitare gli aggiornamenti del progetto, usare un `NoUpgrade` valore:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Cache e estendibilità del progetto

Per migliorare le prestazioni quando si utilizzano soluzioni C++ di grandi dimensioni in Visual Studio 2017, è stata introdotta la [cache del progetto](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) . Viene implementato come database SQLite popolato con i dati del progetto e quindi usato per caricare i progetti senza caricare i progetti MSBuild o CPS in memoria.

Poiché non sono presenti oggetti CPS per i progetti. vcxproj caricati dalla cache, i componenti MEF dell'estensione che importano `UnconfiguredProject` o `ConfiguredProject` non possono essere creati. Per supportare l'estendibilità, la cache del progetto non viene usata quando Visual Studio rileva se un progetto USA o meno le estensioni MEF.

Questi tipi di progetto sono sempre completamente caricati e contengono oggetti CPS in memoria, quindi vengono create tutte le estensioni MEF:

- Progetti di avvio

- Progetti che dispongono di un aggiornamento del progetto personalizzato, ovvero definiscono una `VCProjectUpgraderObjectName` Proprietà

- I progetti che non fanno riferimento a finestre desktop, ovvero definiscono una `ApplicationType` Proprietà

- Progetti di elementi condivisi (con estensione vcxitems) e qualsiasi progetto che vi fa riferimento mediante l'importazione di progetti vcxitems.

Se non viene rilevata nessuna di queste condizioni, viene creata una cache del progetto. La cache include tutti i dati del progetto MSBuild necessari per rispondere alle `get` query sulle `VCProjectEngine` interfacce. Questo significa che tutte le modifiche apportate a livello di file delle proprietà e delle destinazioni di MSBuild eseguite da un'estensione dovrebbero funzionare solo nei progetti caricati dalla cache.

## <a name="shipping-your-extension"></a>Spedizione dell'estensione

Per informazioni su come creare file VSIX, vedere la pagina relativa alla [distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Per informazioni su come aggiungere file a percorsi di installazione speciali, ad esempio per aggiungere file in `$(VCTargetsPath)` , vedere [installazione all'esterno della cartella Extensions](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Risorse aggiuntive

Microsoft Build System ([MSBuild](../msbuild/msbuild.md)) fornisce il motore di compilazione e il formato basato su XML estendibile per i file di progetto. È necessario conoscere i concetti di base di [MSBuild](../msbuild/msbuild-concepts.md) e il modo in cui [MSBuild per Visual C++](/cpp/build/reference/msbuild-visual-cpp-overview) funziona per estendere il sistema del progetto Visual C++.

Il Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) fornisce le API di estensione utilizzate da CPS e dal sistema del progetto Visual C++. Per una panoramica del modo in cui MEF viene usato da CPS, vedere [CPS e MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) nella [Panoramica di VSProjectSystem di MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

È possibile personalizzare il sistema di compilazione esistente per aggiungere passaggi di compilazione o nuovi tipi di file. Per ulteriori informazioni, vedere [Panoramica di MSBuild (Visual C++)](/cpp/build/reference/msbuild-visual-cpp-overview) e [utilizzo delle proprietà del progetto](/cpp/build/working-with-project-properties).
