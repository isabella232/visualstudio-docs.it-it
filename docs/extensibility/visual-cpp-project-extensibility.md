---
description: Il Visual C++ di progetto viene usato per i file con estensione vcxproj.
title: Visual C++ estendibilità del progetto
ms.date: 04/23/2019
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c57e285e939825f70762a8b9edb0dbda258acac8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056732"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio Estendibilità Project sistema e integrazione del set di strumenti C++

Il Visual C++ di progetto viene usato per i file con estensione vcxproj. Si basa sull'Visual Studio [Common Project System (CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) e fornisce altri punti di estendibilità specifici di C++ per una facile integrazione di nuovi set di strumenti, architetture di compilazione e piattaforme di destinazione.

## <a name="c-msbuild-targets-structure"></a>Struttura delle destinazioni MSBuild C++

Tutti i file con estensione vcxproj importano questi file:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Questi file definiscono poco da soli. Importano invece altri file in base ai valori delle proprietà seguenti:

- `$(ApplicationType)`

   Esempi: Windows Store, Android, Linux

- `$(ApplicationTypeRevision)`

   Deve essere una stringa di versione valida nel formato major.minor[.build[.revision]].

   Esempi: 1.0, 10.0.0.0

- `$(Platform)`

   Architettura di compilazione, denominata "Piattaforma" per motivi cronologici.

   Esempi: Win32, x86, x64, ARM

- `$(PlatformToolset)`

   Esempi: v140, v141, v141_xp, llvm

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

La `$(VCTargetsPath)` \\ *cartella Platforms* \\ viene usata quando è `$(ApplicationType)` vuota, per i Windows Desktop.

### <a name="add-a-new-platform-toolset"></a>Aggiungere un nuovo set di strumenti della piattaforma

Per aggiungere un nuovo set di strumenti, ad esempio "MyToolset" per la piattaforma Win32 esistente, creare una cartella *MyToolset* in `$(VCTargetsPath)` *\\ Piattaforme \\ Win32 \\ PlatformToolsets \\* e creare i file *Toolset.props* e *Toolset.targets.*

Ogni nome di cartella in *PlatformToolsets* viene visualizzato nella  finestra di dialogo **Proprietà** Project come set di strumenti della piattaforma disponibile per la piattaforma specificata, come illustrato di seguito:

![Proprietà Del set di strumenti della piattaforma nella finestra di dialogo Pagine delle proprietà del progetto](media/vc-project-extensibility-platform-toolset-property.png "Proprietà Del set di strumenti della piattaforma nella finestra di dialogo Pagine delle proprietà del progetto")

Creare cartelle *MyToolset* simili *e file Toolset.props* e *Toolset.targets* in ogni cartella della piattaforma esistente supportata da questo set di strumenti.

### <a name="add-a-new-platform"></a>Aggiungere una nuova piattaforma

Per aggiungere una nuova piattaforma, ad esempio "MyPlatform", creare una cartella *MyPlatform* in Piattaforme `$(VCTargetsPath)` *\\ \\* e creare i file *Platform.default.props*, *Platform.props* e *Platform.targets* al suo contenuto. Creare anche una `$(VCTargetsPath)` *\\ cartella Platforms \\*<strong><em>MyPlatform</em></strong>*\\ PlatformToolsets \\* e crearne almeno un set di strumenti.

Tutti i nomi di cartella nella *cartella Piattaforme* per ogni e vengono `$(ApplicationType)` visualizzati `$(ApplicationTypeRevision)` nell'IDE come opzioni **piattaforma** disponibili per un progetto.

![Opzione Nuova piattaforma nella finestra di dialogo Nuova Project piattaforma](media/vc-project-extensibility-new-project-platform.png "Opzione Nuova piattaforma nella finestra di dialogo Nuova Project piattaforma")

### <a name="add-a-new-application-type"></a>Aggiungere un nuovo tipo di applicazione

Per aggiungere un nuovo tipo di applicazione, creare una *cartella MyApplicationType* in Tipo `$(VCTargetsPath)` *\\ \\* di applicazione e crearne un file *Defaults.props.* È necessaria almeno una revisione per un tipo di applicazione, quindi creare anche una cartella `$(VCTargetsPath)` *\\ Application \\ Type MyApplicationType \\ 1.0* e crearne un file *Defaults.props.* È anche necessario creare una `$(VCTargetsPath)` *\\ cartella ApplicationType \\ MyApplicationType \\ 1.0 \\ Platforms* e crearvi almeno una piattaforma.

`$(ApplicationType)` le `$(ApplicationTypeRevision)` proprietà e non sono visibili nell'interfaccia utente. Sono definiti nei modelli di progetto e non possono essere modificati dopo la creazione del progetto.

## <a name="the-vcxproj-import-tree"></a>Albero delle importazioni con estensione vcxproj

Un albero semplificato delle importazioni per i file di proprietà e destinazioni di Microsoft C++ è simile al seguente:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore* \\ *Valore* \\ \* predefinito. *props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Tipo di applicazione* \\ `$(ApplicationType)` \\ *Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Tipo di applicazione* \\ `$(ApplicationType)` \\ `$(ApplicationTypeRevision)` \\ *Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Tipo di applicazione* \\ `$(ApplicationType)` \\ `$(ApplicationTypeRevision)` \\  \\ `$(Platform)` Piattaforme \\ *Platform.default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\ *Valore* \\ \* predefinito. *props*

Windows I progetti desktop non definiscono `$(ApplicationType)` , quindi importano solo

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore* \\ *Valore* \\ \* predefinito. *props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\ \\ `$(Platform)` Piattaforme \\ *Platform.default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\ *Valore* \\ \* predefinito. *props*

Si userà la proprietà `$(_PlatformFolder)` per contenere i percorsi `$(Platform)` delle cartelle della piattaforma. Questa proprietà è

> `$(VCTargetsPath)`\\*Piattaforme*\\`$(Platform)`

per Windows desktop e

> `$(VCTargetsPath)`\\*Tipo di applicazione* \\ `$(ApplicationType)` \\ `$(ApplicationTypeRevision)` \\ *Piattaforme*\\`$(Platform)`

per tutto il resto.

I file props vengono importati nell'ordine seguente:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore* \\ \* . *props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets* \\ `$(PlatformToolset)` \\ *Toolset.props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* . *props*

I file di destinazione vengono importati nell'ordine seguente:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Current.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore* \\ \* . *destinazioni* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets* \\ `$(PlatformToolset)` \\ *Toolset.target* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* . *destinazioni*

Se è necessario definire alcune proprietà predefinite per il set di strumenti, è possibile aggiungere file alle cartelle ImportBefore e ImportAfter appropriate.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Creare file Toolset.props e Toolset.targets

*I file Toolset.props* e *Toolset.targets* hanno il controllo completo su cosa accade durante una compilazione quando viene usato questo set di strumenti. Possono anche controllare i debugger disponibili, parte dell'interfaccia utente dell'IDE, ad esempio il contenuto della finestra di dialogo Pagine delle proprietà e alcuni altri aspetti del comportamento del progetto. 

Anche se un set di strumenti può eseguire l'override dell'intero processo di compilazione, in genere si vuole solo modificare o aggiungere alcune istruzioni di compilazione o usare strumenti di compilazione diversi come parte di un processo di compilazione esistente. Per raggiungere questo obiettivo, sono disponibili diversi file di proprietà e destinazioni comuni che il set di strumenti può importare. A seconda dell'operazione che si vuole eseguire nel set di strumenti, questi file possono essere utili per l'uso come importazioni o come esempi:

- `$(VCTargetsPath)`\\*Microsoft.CppCommon.targets*

  Questo file definisce le parti principali del processo di compilazione nativo e importa anche:

  - `$(VCTargetsPath)`\\*Microsoft.CppBuild.targets*

  - `$(VCTargetsPath)`\\*Microsoft.BuildSteps.targets*

  - `$(MSBuildToolsPath)`\\*Microsoft.Common.Targets*

- `$(VCTargetsPath)`\\*Microsoft.Cpp.Common.props*

   Imposta le impostazioni predefinite per i set di strumenti che usano i compilatori Microsoft e i criteri di Windows.

- `$(VCTargetsPath)`\\*Microsoft.Cpp.WindowsSDK.props*

   Questo file determina il percorso Windows SDK e definisce alcune proprietà importanti per le app che hanno come destinazione Windows.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Integrare destinazioni specifiche del set di strumenti con il processo di compilazione C++ predefinito

Il processo di compilazione C++ predefinito è definito in *Microsoft.CppCommon.targets*. Le destinazioni non chiamano strumenti di compilazione specifici. specificano le istruzioni di compilazione principali, l'ordine e le dipendenze.

La build C++ include tre passaggi principali, rappresentati dalle destinazioni seguenti:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Poiché ogni istruzione di compilazione può essere eseguita in modo indipendente, le destinazioni in esecuzione in un passaggio non possono basarsi sui gruppi di elementi e sulle proprietà definiti nelle destinazioni eseguite come parte di un passaggio diverso. Questa divisione consente determinate ottimizzazioni delle prestazioni di compilazione. Anche se non viene usato per impostazione predefinita, è comunque consigliato rispettare questa separazione.

Le destinazioni eseguite all'interno di ogni passaggio sono controllate da queste proprietà:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Ogni passaggio include anche le proprietà Before e After.

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

Per esempi delle destinazioni incluse in ogni passaggio, vedere il file *Microsoft.CppBuild.targets:*

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Se si osservano le destinazioni, ad esempio , si scoprirà che non esereranno direttamente da sole, ma dipendono invece da `_ClCompile` altre destinazioni, tra cui `ClCompile` :

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` e altre destinazioni specifiche dello strumento di compilazione sono definite come destinazioni vuote in *Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"/>
```

Poiché la destinazione è vuota, a meno che non venga sottoposta a override da un set di strumenti, non viene eseguita alcuna `ClCompile` azione di compilazione reale. Le destinazioni del set di strumenti possono eseguire l'override della destinazione, ad esempio possono contenere un'altra definizione dopo l'importazione `ClCompile` `ClCompile` di *Microsoft.CppBuild.targets:*

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Nonostante il nome, creato prima Visual Studio supporto multipiattaforma, la destinazione non deve chiamare `ClCompile` CL.exe. Può anche chiamare Clang, gcc o altri compilatori usando le attività di MSBuild appropriate.

La destinazione non deve avere dipendenze tranne la destinazione, che è necessaria per il funzionamento del comando di compilazione a file singolo `ClCompile` `SelectClCompile` nell'IDE.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>MSBuild attività da usare nelle destinazioni del set di strumenti

Per richiamare uno strumento di compilazione effettivo, la destinazione deve chiamare un'MSBuild attività. È disponibile [un'attività Exec di](../msbuild/exec-task.md) base che consente di specificare una riga di comando da eseguire. Tuttavia, gli strumenti di compilazione in genere hanno molte opzioni, input. e gli output da rilevare per le compilazioni incrementali, quindi è più opportuno avere attività speciali. Ad esempio, l'attività converte MSBuild proprietà in opzioni CL.exe, le scrive in un file di risposta e chiama `CL` CL.exe. Tiene inoltre traccia di tutti i file di input e di output per le compilazioni incrementali successive. Per altre informazioni, vedere [Compilazioni incrementali](#incremental-builds-and-up-to-date-checks)e controlli aggiornati.

Il Microsoft.Cpp.Common.Tasks.dll implementa queste attività:

- `BSCMake`

- `CL`

- `ClangCompile` (opzioni clang-gcc)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (ad esempio Exec ma con rilevamento di input e output)

- `SetEnv`

- `GetOutOfDateItems`

Se si dispone di uno strumento che esegue la stessa azione di uno strumento esistente e che dispone di opzioni della riga di comando simili (come fanno clang-cl e CL), è possibile usare la stessa attività per entrambi.

Se è necessario creare una nuova attività per uno strumento di compilazione, è possibile scegliere tra le opzioni seguenti:

1. Se si usa questa attività raramente o se alcuni secondi non sono importanti per la compilazione, è possibile usare MSBuild attività "inline":

   - Attività Xaml (una regola di compilazione personalizzata)

     Per un esempio di dichiarazione di attività Xaml, vedere BuildCustomizationsmasm.xmle per il relativo utilizzo, vedere `$(VCTargetsPath)` \\  \\ ** `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.targets*.

   - [Attività Codice](../msbuild/msbuild-inline-tasks.md)

1. Se si vuole migliorare le prestazioni delle attività o è sufficiente una funzionalità più complessa, usare il normale MSBuild [di scrittura delle](../msbuild/task-writing.md) attività.

   Se non tutti gli input e gli output dello strumento sono elencati nella riga di comando dello strumento, come nei casi , e e se si desidera il rilevamento automatico dei file di input e di output e la creazione di file con estensione `CL` `MIDL` `RC` tlog, derivare l'attività dalla `Microsoft.Build.CPPTasks.TrackedVCToolTask` classe . Attualmente, mentre è disponibile la documentazione per la classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) di base, non sono disponibili esempi o documentazione per i dettagli della `TrackedVCToolTask` classe. Se questo è particolarmente interessante, aggiungere la voce a una richiesta in [Developer Community](https://aka.ms/feedback/suggest?space=62).

## <a name="incremental-builds-and-up-to-date-checks"></a>Compilazioni incrementali e controlli aggiornati

Il valore predefinito MSBuild le destinazioni di compilazione incrementali usano `Inputs` gli `Outputs` attributi e . Se vengono specificati, MSBuild la destinazione solo se uno degli input ha un timestamp più recente rispetto a tutti gli output. Poiché i file di origine spesso includono o importano altri file e gli strumenti di compilazione producono output diversi a seconda delle opzioni degli strumenti, è difficile specificare tutti gli input e gli output possibili nelle destinazioni MSBuild destinazione.

Per gestire questo problema, la compilazione C++ usa una tecnica diversa per supportare le compilazioni incrementali. La maggior parte delle destinazioni non specifica input e output e di conseguenza viene sempre eseguita durante la compilazione. Le attività chiamate dalle destinazioni scrivono informazioni su tutti gli input e gli output in *file tlog* con estensione tlog. I file con estensione tlog vengono usati dalle compilazioni successive per controllare cosa è cambiato e deve essere ricompilato e ciò che è aggiornato. I file con estensione tlog sono anche l'unica origine per il controllo predefinito aggiornato della compilazione nell'IDE.

Per determinare tutti gli input e gli output, le attività degli strumenti nativi usano tracker.exe e la classe [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) fornita da MSBuild.

Microsoft.Build.CPPTasks.Common.dll definisce la classe `TrackedVCToolTask` di base astratta pubblica. La maggior parte delle attività dello strumento nativo deriva da questa classe.

A partire Visual Studio 2017 update 15.8, è possibile usare l'attività implementata in Microsoft.Cpp.Common.Tasks.dll per produrre file con estensione tlog per destinazioni personalizzate con input e `GetOutOfDateItems` output noti.
In alternativa, è possibile crearli usando `WriteLinesToFile` l'attività . Vedere la `_WriteMasmTlogs` destinazione in `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.targets* come esempio.

## <a name="tlog-files"></a>File con estensione tlog

Esistono tre tipi di file con estensione tlog: *lettura,* *scrittura* e *riga di comando.* I file con estensione tlog di lettura e scrittura vengono usati dalle compilazioni incrementali e dal controllo aggiornato nell'IDE. I file con estensione tlog della riga di comando vengono usati solo nelle compilazioni incrementali.

MSBuild fornisce queste classi helper per leggere e scrivere file con estensione tlog:

- [Canonicaltrackedinputfiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [Canonicaltrackedoutputfiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

La [classe FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) può essere usata per accedere ai file con estensione tlog di lettura e scrittura e identificare gli input più nuovi degli output o se manca un output. Viene usato nel controllo aggiornato.

I file con estensione tlog della riga di comando contengono informazioni sulle righe di comando usate nella compilazione. Vengono usati solo per le compilazioni incrementali, non per i controlli aggiornati, quindi il formato interno è determinato dall'attività MSBuild che li produce.

### <a name="read-tlog-format"></a>Leggere il formato con estensione tlog

*Leggere* i file con estensione tlog ( \* .read. \* . tlog) contengono informazioni sui file di origine e sulle relative dipendenze.

Un punto di interruzione ( **^** ) all'inizio di una riga indica una o più origini. Le origini che condividono le stesse dipendenze sono separate da una barra verticale ( **\|** ).

I file di dipendenza sono elencati dopo le origini, ognuno nella propria riga. Tutti i nomi di file sono percorsi completi.

Si supponga, ad esempio, che le origini del progetto siano disponibili in *F: \\ test \\ ConsoleApplication1 \\ ConsoleApplication1*. Se il file di *origine, Class1.cpp,* include,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

quindi il file *CL.read.1.tlog* contiene il file di origine seguito dalle due dipendenze:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Non è necessario scrivere nomi di file in maiuscolo, ma è una comodità per alcuni strumenti.

### <a name="write-tlog-format"></a>Scrivere il formato TLOG

*Scrivere* .tlog ( \* .write. \* . tlog) i file connettono origini e output.

Un punto di interruzione ( **^** ) all'inizio di una riga indica una o più origini. Più origini sono separate da una barra verticale ( **\|** ).

I file di output compilati dalle origini devono essere elencati dopo le origini, ognuno sulla propria riga. Tutti i nomi di file devono essere percorsi completi.

Ad esempio, per un semplice progetto ConsoleApplication con un file di origine *aggiuntivo Class1.cpp,* il file *link.write.1.tlog* può contenere:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Compilazione in fase di progettazione

Nell'IDE i progetti vcxproj usano un set di destinazioni MSBuild per ottenere informazioni aggiuntive dal progetto e per rigenerare i file di output. Alcune di queste destinazioni vengono usate solo nelle compilazioni in fase di progettazione, ma molte di esse vengono usate sia nelle compilazioni normali che nelle compilazioni in fase di progettazione.

Per informazioni generali sulle compilazioni in fase di progettazione, vedere la documentazione di CPS per [le compilazioni in fase di progettazione](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Questa documentazione è applicabile solo in parte Visual C++ progetti.

Le destinazioni e indicate nella documentazione relativa alle compilazioni in fase di progettazione `CompileDesignTime` non vengono mai eseguite per i progetti `Compile` vcxproj. Visual C++ progetti con estensione vcxproj usano destinazioni in fase di progettazione diverse per ottenere informazioni IntelliSense.

### <a name="design-time-targets-for-intellisense-information"></a>Destinazioni in fase di progettazione per informazioni intelliSense

Le destinazioni della fase di progettazione usate nei progetti vcxproj sono definite in `$(VCTargetsPath)` \\ *Microsoft.Cpp.DesignTime.targets*.

La `GetClCommandLines` destinazione raccoglie le opzioni del compilatore per IntelliSense:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` : destinazioni solo in fase di progettazione, necessarie per l'inizializzazione della compilazione in fase di progettazione. Tra le altre cose, queste destinazioni disabilitano alcune delle normali funzionalità di compilazione per migliorare le prestazioni.

- `ComputeCompileInputsTargets` : set di destinazioni che modifica le opzioni e gli elementi del compilatore. Queste destinazioni vengono eseguite sia in fase di progettazione che in compilazioni regolari.

La destinazione chiama `CLCommandLine` l'attività per creare la riga di comando da usare per IntelliSense. Anche in questo caso, nonostante il nome, può gestire non solo le opzioni CL, ma anche le opzioni Clang e gcc. Il tipo delle opzioni del compilatore è controllato dalla `ClangMode` proprietà .

Attualmente, la riga di comando prodotta dall'attività usa sempre le opzioni CL (anche in modalità Clang) perché sono più facili da analizzare per il motore `CLCommandLine` IntelliSense.

Se si aggiunge una destinazione che viene eseguita prima della compilazione, sia normale che in fase di progettazione, assicurarsi che non interrompa le compilazioni in fase di progettazione o influisca sulle prestazioni. Il modo più semplice per testare la destinazione è aprire un prompt dei comandi per sviluppatori ed eseguire questo comando:

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

Questo comando genera un log di compilazione dettagliato, *msbuild.log*, con un riepilogo delle prestazioni per le destinazioni e le attività alla fine.

Assicurarsi di usare in tutte le operazioni che hanno senso solo `Condition ="'$(DesignTimeBuild)' != 'true'"` per le compilazioni regolari e non per le compilazioni in fase di progettazione.

### <a name="design-time-targets-that-generate-sources"></a>Destinazioni in fase di progettazione che generano origini

*Questa funzionalità è disabilitata per impostazione predefinita per i progetti nativi desktop e non è attualmente supportata nei progetti memorizzati nella cache.*

Se i metadati sono definiti per un elemento di progetto, la destinazione viene eseguita automaticamente sia al caricamento del progetto che alla modifica `GeneratorTarget` del file di origine.

::: moniker range="vs-2017"

Ad esempio, per generare automaticamente file con estensione cpp o h da file con estensione xaml, l'MSBuild `$(VSInstallDir)` \\  \\ *Microsoft* \\ *WindowsXaml* \\ *v15.0* \\ \* \\ *Microsoft.Windows. Ui. I file Xaml.CPP.Targets* definiscono queste entità:

::: moniker-end

::: moniker range=">=vs-2019"

Ad esempio, per generare automaticamente file con estensione cpp o h da file con estensione xaml, MSBuild `$(VSInstallDir)` \\  \\ *Microsoft* \\ *WindowsXaml* \\ *v16.0* \\ \* \\ *Microsoft.Windows. Ui. I file Xaml.CPP.Targets* definiscono queste entità:

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

Per usare per ottenere il contenuto non salvato dei file di origine, le destinazioni e l'attività devono essere registrate come `Task.HostObject` [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017&preserve-view=true) per i progetti specifici in un pkgdef:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual C++ estendibilità del progetto nell'IDE Visual Studio

Il Visual C++ di progetto è basato su [VS Project System](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)e usa i relativi punti di estendibilità. Tuttavia, l'implementazione della gerarchia del progetto è specifica Visual C++ e non basata su CPS, quindi l'estendibilità della gerarchia è limitata agli elementi del progetto.

### <a name="project-property-pages"></a>Pagina delle proprietà del progetto

Per informazioni generali sulla progettazione, vedere [Framework Multi-Targeting for VC++ Projects](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/).

In parole semplici, le pagine delle proprietà che vengono visualizzati nella finestra **Project proprietà** per un progetto C++ sono definite dai *file delle* regole. Un file di regole specifica un set di proprietà da visualizzare in una pagina delle proprietà e come e dove devono essere salvate nel file di progetto. I file delle regole .xml che usano il formato Xaml. I tipi usati per serializzarli sono descritti in [Microsoft.Build.Framework.XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes). Per altre informazioni sull'uso dei file delle regole nei progetti, vedere [File di regole XML della pagina delle proprietà](/cpp/build/reference/property-page-xml-files).

I file delle regole devono essere aggiunti al gruppo `PropertyPageSchema` di elementi:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` i metadati limitano la visibilità della regola, che è controllata anche dal tipo di regola e può avere uno di questi valori:

`Project` | `File` | `PropertySheet`

CPS supporta altri valori per il tipo di contesto, ma non vengono usati nei Visual C++ progetto.

Se la regola deve essere visibile in più contesti, usare i punti e virgola (**;**) per separare i valori di contesto, come illustrato di seguito:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Formato delle regole e tipi principali

Il formato della regola è semplice, quindi questa sezione descrive solo gli attributi che influiscono sull'aspetto della regola nell'interfaccia utente.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

`PageTemplate`L'attributo definisce la modalità di visualizzazione della regola nella finestra di dialogo Pagine **delle** proprietà. L'attributo può avere uno dei valori seguenti:

| Attributo | Descrizione |
|------------| - |
| `generic` | Tutte le proprietà vengono visualizzate in una pagina in Intestazioni categoria<br/>La regola può essere visibile per `Project` i `PropertySheet` contesti e , ma non `File` per .<br/><br/> Esempio: `$(VCTargetsPath)` \\ *1033* \\ *general.xml* |
| `tool` | Le categorie vengono visualizzate come pagine secondarie.<br/>La regola può essere visibile in tutti i contesti: `Project` e `PropertySheet` `File` .<br/>La regola è visibile in Project solo se il progetto include elementi con definito in , a meno che il nome della regola non sia `ItemType` `Rule.DataSource` incluso nel `ProjectTools` gruppo di elementi.<br/><br/>Esempio: `$(VCTargetsPath)` \\ *1033* \\ *clang.xml* |
| `debugger` | La pagina viene visualizzata come parte della pagina Debug.<br/>Le categorie vengono attualmente ignorate.<br/>Il nome della regola deve corrispondere all'attributo dell'oggetto MEF dell'utilità di avvio `ExportDebugger` del debug.<br/><br/>Esempio: `$(VCTargetsPath)` \\ *1033* \\ *debugger local \_ \_windows.xml* |
| *Personalizzato* | Modello personalizzato. Il nome del modello deve corrispondere `ExportPropertyPageUIFactoryProvider` all'attributo `PropertyPageUIFactoryProvider` dell'oggetto MEF. Vedere **Microsoft.VisualStudio.ProjectSystem.Designers.Properties.IPropertyPageUIFactoryProvider**.<br/><br/> Esempio: `$(VCTargetsPath)` \\ *1033* \\ *userMacros.xml* |

Se la regola usa uno dei modelli basati su Griglia delle proprietà, può usare questi punti di estendibilità per le relative proprietà:

- [Editor di valori di proprietà](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Provider di valori di enumerazione dinamici](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Estendere una regola

Se si vuole usare una regola esistente, ma è necessario aggiungere o rimuovere (ovvero nascondere) solo alcune proprietà, è possibile creare una regola [di estensione](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Eseguire l'override di una regola

È possibile che il set di strumenti usi la maggior parte delle regole predefinite del progetto, ma che ne sostituisca solo una o alcune. Si supponga, ad esempio, di voler modificare solo la regola C/C++ per visualizzare opzioni del compilatore diverse. È possibile specificare una nuova regola con lo stesso nome e nome visualizzato della regola esistente e includerla nel gruppo di elementi dopo l'importazione delle destinazioni `PropertyPageSchema` cpp predefinite. Nel progetto viene usata una sola regola con un nome specifico e l'ultima inclusa nel gruppo `PropertyPageSchema` di elementi viene vinca.

#### <a name="project-items"></a>Elementi di progetto

Il file *ProjectItemsSchema.xml* definisce i valori e per Gli elementi trattati come elementi Project e definisce gli elementi per determinare a quale gruppo di elementi viene aggiunto un nuovo `ContentType` `ItemType` `FileExtension` file.

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

Nel file targets aggiungere quindi:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Esempio: `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.xml*

### <a name="debuggers"></a>Debugger

Il servizio Debug in Visual Studio supporta l'estendibilità per il motore di debug. Per altre informazioni, vedere questi esempi:

- [MIEngine, open source che supporta il debug lldb](https://github.com/Microsoft/MIEngine)

- [Visual Studio di motore di debug](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Per specificare i motori di debug e altre proprietà per la sessione di debug, è necessario implementare un componente [MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) dell'utilità di avvio del debug e aggiungere una `debugger` regola. Per un esempio, vedere il `$(VCTargetsPath)` \\ filewindows.xml debugger \\ 1033. \_ \_

### <a name="deploy"></a>Distribuisci

I progetti vcxproj usano l'Visual Studio Project estendibilità del sistema per [distribuire i provider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Compilare un controllo aggiornato

Per impostazione predefinita, il controllo di compilazione aggiornato richiede la lettura di file con estensione tlog e la scrittura di file con estensione tlog nella cartella durante la compilazione per tutti gli input e gli `$(TlogLocation)` output di compilazione.

Per usare un controllo aggiornato personalizzato:

1. Disabilitare il controllo aggiornato predefinito aggiungendo la funzionalità `NoVCDefaultBuildUpToDateCheckProvider` nel file *Toolset.targets:*

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Implementare un [IBuildUpToDateCheckProvider personalizzato.](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md)

## <a name="project-upgrade"></a>Project aggiornamento

### <a name="default-vcxproj-project-upgrader"></a>Strumento di aggiornamento del progetto vcxproj predefinito

Lo strumento di aggiornamento del progetto vcxproj predefinito modifica la versione del set di MSBuild e `PlatformToolset` `ApplicationTypeRevision` .NET Framework. Le ultime due vengono sempre modificate con le impostazioni Visual Studio versione predefinita, ma possono essere controllate da proprietà MSBuild `PlatformToolset` `ApplicationTypeRevision` speciali.

Lo upgrader usa questi criteri per decidere se un progetto può essere aggiornato o meno:

1. Per i progetti che definiscono e , è presente una cartella con un numero di revisione superiore a `ApplicationType` `ApplicationTypeRevision` quello corrente.

1. La proprietà è definita per il set di strumenti corrente e il relativo `_UpgradePlatformToolsetFor_<safe_toolset_name>` valore non è uguale al set di strumenti corrente.

   In questi nomi di proprietà rappresenta il nome del set di strumenti con tutti *\<safe_toolset_name>* i caratteri non alfanumerici sostituiti da un carattere di sottolineatura ( **\_** ).

Quando un progetto può essere aggiornato, partecipa al ridestinazione *della soluzione*. Per altre informazioni, vedere [IVsTrackProjectRetargeting2.](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2)

Se si vuole adornare i nomi dei progetti **Esplora soluzioni** quando i progetti usano un set di strumenti specifico, definire una `_PlatformToolsetShortNameFor_<safe_toolset_name>` proprietà.

Per esempi di `_UpgradePlatformToolsetFor_<safe_toolset_name>` `_PlatformToolsetShortNameFor_<safe_toolset_name>` definizioni di proprietà e , vedere il file *Microsoft.Cpp.Default.props.* Per esempi di utilizzo, vedere il file `$(VCTargetPath)` \\ *Microsoft.Cpp.Platform.targets.*

### <a name="custom-project-upgrader"></a>Strumento di aggiornamento del progetto personalizzato

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

Il codice può importare e chiamare l'oggetto dello strumento di aggiornamento vcxproj predefinito:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` è definito *in* Microsoft.VisualStudio.ProjectSystem.VS.dlled è simile a `IVsRetargetProjectAsync` .

Definire la `VCProjectUpgraderObjectName` proprietà per indicare al sistema del progetto di usare l'oggetto dell'upgrader personalizzato:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Disabilitare l'aggiornamento del progetto

Per disabilitare gli aggiornamenti del progetto, usare un `NoUpgrade` valore:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Project cache ed estendibilità

Per migliorare le prestazioni quando si lavora con soluzioni C++ di grandi dimensioni Visual Studio 2017, è stata introdotta la [cache](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) del progetto. Viene implementato come database SQLite popolato con i dati del progetto e quindi usato per caricare i progetti senza caricare i progetti MSBuild o CPS in memoria.

Poiché non sono presenti oggetti CPS per i progetti vcxproj caricati dalla cache, i componenti MEF dell'estensione che importano o `UnconfiguredProject` `ConfiguredProject` non possono essere creati. Per supportare l'estendibilità, la cache del progetto non viene usata quando Visual Studio rileva se un progetto usa (o è probabile che usi) le estensioni MEF.

Questi tipi di progetto vengono sempre caricati completamente e hanno oggetti CPS in memoria, quindi vengono create tutte le estensioni MEF:

- Progetti di avvio

- I progetti con uno strumento di aggiornamento del progetto personalizzato, ad esempio, definiscono una `VCProjectUpgraderObjectName` proprietà

- I progetti che non hanno come destinazione desktop Windows, ad esempio definiscono una `ApplicationType` proprietà

- Progetti di elementi condivisi (con estensione vcxitems) e tutti i progetti che fanno riferimento a essi tramite l'importazione di progetti vcxitems.

Se nessuna di queste condizioni viene rilevata, viene creata una cache del progetto. La cache include tutti i dati del progetto MSBuild necessario per rispondere `get` alle query `VCProjectEngine` sulle interfacce. Ciò significa che tutte le modifiche a livello MSBuild di file di proprietà e destinazioni eseguite da un'estensione devono funzionare solo nei progetti caricati dalla cache.

## <a name="shipping-your-extension"></a>Spedizione dell'estensione

Per informazioni su come creare file VSIX, vedere [Shipping Visual Studio Extensions](../extensibility/shipping-visual-studio-extensions.md). Per informazioni su come aggiungere file a percorsi di installazione speciali, ad esempio per aggiungere file in , vedere `$(VCTargetsPath)` Installazione all'esterno della cartella [extensions](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Risorse aggiuntive

Microsoft Build System ([MSBuild](../msbuild/msbuild.md)) fornisce il motore di compilazione e il formato estendibile basato su XML per i file di progetto. È necessario avere [](../msbuild/msbuild-concepts.md) familiarità con i concetti MSBuild di base e con il funzionamento di [MSBuild per Visual C++](/cpp/build/reference/msbuild-visual-cpp-overview) per estendere il sistema Visual C++ progetto.

Il Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) fornisce le API di estensione usate da CPS e dal Visual C++ di progetto. Per una panoramica dell'uso di MEF da parte di CPS, vedere [CPS e MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) nella panoramica [di VSProjectSystem di MEF.](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md)

È possibile personalizzare il sistema di compilazione esistente per aggiungere istruzioni di compilazione o nuovi tipi di file. Per altre informazioni, vedere [Panoramica MSBuild (Visual C++)](/cpp/build/reference/msbuild-visual-cpp-overview) e [Uso delle proprietà del progetto](/cpp/build/working-with-project-properties).
