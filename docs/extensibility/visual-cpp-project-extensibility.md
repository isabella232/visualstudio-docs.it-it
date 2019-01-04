---
title: Estensibilità di progetto Visual C++
ms.date: 09/12/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0eccf13f38799c1d35b7fe4226fa02ec1a291b0c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986986"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio C++ sistema estendibilità e set di strumenti di integrazione di Project

Il *sistema di progetto Visual C++* viene usato per i file con estensione vcxproj. Si basa il [Visual Studio Common Project System (CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) e fornisce ulteriori, dei punti di estendibilità di specifiche di C++ per semplificare l'integrazione di nuovi set di strumenti, le architetture di compilazione e le piattaforme di destinazione. 

## <a name="c-msbuild-targets-structure"></a>Struttura di destinazioni MSBuild C++

Tutti i file con estensione vcxproj importare questi file:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Questi file definiscono poco da soli. Invece di importare altri file basati su valori di queste proprietà:

- `$(ApplicationType)`

   Esempi: Windows Store, Android, Linux

- `$(ApplicationTypeRevision)`

   Deve essere una stringa di versione valida, il modulo Revision]].

   Esempi: le versioni 1.0, 10.0.0.0

- `$(Platform)`

   L'architettura di compilazione, denominata "Piattaforma" per motivi cronologici.

   Esempi: Win32, x86, x64, ARM   

- `$(PlatformToolset)`

   Esempi: v140, v141, v141_xp, llvm

Questi valori di proprietà specificano i nomi delle cartelle sotto la `$(VCTargetsPath)` cartella radice:

> `$(VCTargetsPath)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;*Tipo di applicazione*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Piattaforme*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets set*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`  
> &nbsp;&nbsp;&nbsp;&nbsp;Piattaforme\\&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(utilizzato quando `$(ApplicationType)` è vuoto, per i progetti Desktop di Windows)  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets set*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`  

### <a name="add-a-new-platform-toolset"></a>Aggiungere un nuovo set di strumenti della piattaforma

Per aggiungere un nuovo set di strumenti, ad esempio, "MyToolset" per la piattaforma Win32 esistente, creare un *MyToolset* sottocartella `$(VCTargetsPath)`  *\\piattaforme\\Win32\\ PlatformToolsets set\\*e creare *Toolset.props* e *Toolset.targets* file in essa contenuti.

Ogni nome di cartella sotto *PlatformToolsets set* viene visualizzato nel **le proprietà del progetto** finestra di dialogo con una disponibilità **set strumenti della piattaforma** per la piattaforma specificata, come illustrato di seguito:

![La proprietà set di strumenti della piattaforma nella finestra di dialogo Pagine delle proprietà progetto](media/vc-project-extensibility-platform-toolset-property.png "proprietà set di strumenti della piattaforma nella finestra di dialogo Pagine delle proprietà progetto")

Creare simile *MyToolset* cartelle e *Toolset.props* e *Toolset.targets* supporta questo set di strumenti di file in ogni cartella di piattaforma esistente.

### <a name="add-a-new-platform"></a>Aggiungere una nuova piattaforma

Per aggiungere una nuova piattaforma, ad esempio, "MyPlatform", creare un *MyPlatform* sottocartella `$(VCTargetsPath)`  *\\piattaforme\\*e creare  *Platform.default.props*, *Platform.props*, e *Platform.targets* file in essa contenuti. Creare anche un `$(VCTargetsPath)`  *\\piattaforme\\*<strong><em>MyPlatform</em></strong>*\\PlatformToolsets set\\*  cartella e creare almeno un set di strumenti in essa.

Tutti i nomi di cartella sotto la *piattaforme* cartella per ogni `$(ApplicationType)` e `$(ApplicationTypeRevision)` vengono visualizzati nell'IDE come disponibili **piattaforma** scelte per un progetto.

![Nuova piattaforma in uso nella finestra di dialogo nuova piattaforma progetto](media/vc-project-extensibility-new-project-platform.png "la nuova piattaforma in uso nella finestra di dialogo nuova piattaforma progetto")

### <a name="add-a-new-application-type"></a>Aggiungere un nuovo tipo di applicazione

Per aggiungere un nuovo tipo di applicazione, creare un *MyApplicationType* sottocartella `$(VCTargetsPath)` *\\tipo di applicazione\\* e creare un *Defaults.props* file in essa contenuti. Almeno una revisione è necessaria per un tipo di applicazione, pertanto anche creare una `$(VCTargetsPath)`  *\\tipo di applicazione\\MyApplicationType\\1.0* cartella e creare un  *Defaults.props* file in essa contenuti. È consigliabile creare anche un `$(VCTargetsPath)`  *\\ApplicationType\\MyApplicationType\\1.0\\piattaforme* cartella e creare almeno una piattaforma in esso.

`$(ApplicationType)` e `$(ApplicationTypeRevision)` proprietà non sono visibili nell'interfaccia utente. Essi vengono definiti nei modelli di progetto e non può essere modificati dopo la creazione del progetto.


## <a name="the-vcxproj-import-tree"></a>L'albero importato con estensione vcxproj

Simile a una struttura semplificata di imports per i file di proprietà e destinazioni di Microsoft C++:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*predefinito*\\\*. *props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Tipo di applicazione*\\`$(ApplicationType)`\\*Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Tipo di applicazione*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Tipo di applicazione*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*piattaforme* \\ `$(Platform)` \\  *Platform.default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*predefinito*\\\*. *props*  

I progetti Desktop di Windows non definiscono `$(ApplicationType)`, in modo che solo l'importazione

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*predefinito*\\\*. *props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Piattaforme*\\`$(Platform)`\\*Platform.default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*predefinito*\\\*. *props*  

Si userà il `$(_PlatformFolder)` proprietà per contenere il `$(Platform)` percorsi della cartella della piattaforma. Questa proprietà è 

> `$(VCTargetsPath)`\\*Piattaforme*\\`$(Platform)`

per le app Desktop di Windows, e 

> `$(VCTargetsPath)`\\*Tipo di applicazione*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*piattaforme*\\`$(Platform)`

per tutto il resto.

I file props vengono importati nell'ordine indicato:

> `$(VCTargetsPath)`\\*Props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets set*\\`$(PlatformToolset)`\\*Toolset.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*. *props*  

I file di destinazioni vengono importati nell'ordine indicato:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Current.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *destinazioni*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets set*\\`$(PlatformToolset)`\\*Toolset.target*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*. *destinazioni*  

Se è necessario definire alcune proprietà predefinite per il set di strumenti, è possibile aggiungere i file nelle cartelle ImportBefore e ImportAfter appropriate.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>File Toolset.props autore e Toolset.targets

*Toolset.props* e *Toolset.targets* file hanno il controllo completo su ciò che accade durante una compilazione quando si utilizza questo set di strumenti. È inoltre possibile controllare i debugger disponibili, parte dell'interfaccia utente IDE, ad esempio, il contenuto nel **pagine delle proprietà** finestra di dialogo e alcuni altri aspetti del comportamento del progetto.

Anche se un set di strumenti è possibile sostituire l'intero processo di compilazione, in genere è sufficiente il set di strumenti per modificare o aggiungere che alcune istruzioni di compilazione o usare gli strumenti di compilazione differente, come parte di un processo di compilazione esistente. Per portare a termine questo obiettivo, esistono una serie di file comuni di proprietà e destinazioni che può importare il set di strumenti. A seconda di ciò che si desidera il set di strumenti per eseguire operazioni, questi file possono risultare utili da usare come importazioni o a livello esemplificativo:

- `$(VCTargetsPath)`\\*Microsoft.CppCommon.targets*

   Questo file definisce le parti principali del processo di compilazione nativa e Importa anche:

   - `$(VCTargetsPath)`\\*Microsoft.CppBuild.targets*

   - `$(VCTargetsPath)`\\*Microsoft.BuildSteps.targets*

   - `$(MSBuildToolsPath)`\\*Microsoftcommon. targets*

- `$(VCTargetsPath)`\\*Microsoft.Cpp.Common.props*

   Imposta valori predefiniti per i set di strumenti che utilizzano i compilatori Microsoft e Windows di destinazione.

- `$(VCTargetsPath)`\\*Microsoft.Cpp.WindowsSDK.props*

   Questo file determina la posizione di Windows SDK e definisce alcune proprietà importanti per le app destinate a Windows.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Integrare le destinazioni specifiche di set di strumenti con il valore predefinito di processo di compilazione C++ 

Il valore predefinito di processo di compilazione di C++ è definito *Microsoft.CppCommon.targets*. Le destinazioni presenti non chiamano qualsiasi strumento di compilazione specifica; specificano i passaggi, l'ordine e le dipendenze di compilazione principale.

La compilazione di C++ ha tre passaggi principali sono rappresentati dalle destinazioni seguenti:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Poiché ogni istruzione di compilazione può essere eseguite in modo indipendente, le destinazioni in esecuzione in un unico passaggio non è possibile si basano sui gruppi di elementi e le proprietà definite nelle destinazioni che vengono eseguiti come parte di diversi passaggi. Questa divisione consente alcune build ottimizzazioni delle prestazioni. Anche se non viene utilizzato per impostazione predefinita, si è ancora invitati a rispettare questa separazione.

Le destinazioni che vengono eseguite all'interno di ogni passaggio vengono controllate da queste proprietà:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Ogni passaggio prevede anche prima e dopo le proprietà. 

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

Vedere le *Microsoft.CppBuild.targets* file per alcuni esempi delle destinazioni incluse in ogni passaggio:

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Se si esamina le destinazioni, ad esempio `_ClCompile`, si noterà che non eseguono alcuna operazione direttamente da soli, ma invece dipendono da altre destinazioni, tra cui `ClCompile`:

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` e altri compilazione di destinazioni specifici dello strumento sono definite come destinazioni vuote in *Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"/>
```

Poiché il `ClCompile` destinazione è vuota, a meno che non venga sottoposto a override da un set di strumenti, viene eseguita alcuna azione di compilazione reale. Le destinazioni di set di strumenti possono eseguire l'override di `ClCompile` di destinazione, vale a dire possono contenere un'altra `ClCompile` definizione dopo l'importazione *Microsoft.CppBuild.targets*: 

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Nonostante il nome, che è stato creato prima di Visual Studio implementato il supporto multipiattaforma, il `ClCompile` destinazione senza dover chiamare CL.exe. Può anche chiamare altri compilatori, Clang e gcc tramite le attività di MSBuild appropriate.

Il `ClCompile` destinazione non deve includere tutte le dipendenze, ad eccezione di `SelectClCompile` destinazione, che è necessaria per il comando di compilazione singolo file per funzionare nell'IDE.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>Attività di MSBuild da usare nelle destinazioni di set di strumenti

Per richiamare uno strumento di compilazione effettiva, la destinazione deve chiamare un'attività MSBuild. È presente una basic [attività Exec](../msbuild/exec-task.md) che consente di specificare una riga di comando da eseguire. Tuttavia, gli strumenti di compilazione hanno in genere molte opzioni, gli input. e gli output per tenere traccia per le compilazioni incrementali, pertanto è più opportuno eseguire attività speciali per loro. Ad esempio, il `CL` attività converte le proprietà di MSBuild in CL.exe commutatori, li scrive in un file di risposta e chiama CL.exe. Tiene inoltre traccia tutti i file di input e outpui per le compilazioni incrementali sono in un secondo momento. Per altre informazioni, vedere [compilazione incrementale e verifica di aggiornamento](#incremental-build-and-up-to-date-check).

Il Microsoft.Cpp.Common.Tasks.dll implementa queste attività:

- `BSCMake`

- `CL`

- `ClangCompile` (commutatori clang-gcc)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (ad esempio Exec ma con input e output di rilevamento)

- `SetEnv`

Se si dispone di uno strumento che esegue la stessa azione di uno strumento esistente e che dispone di simili opzioni della riga di comando (come clang-cl e CL), è possibile usare la stessa operazione per entrambi.

Se è necessario creare una nuova attività per uno strumento di compilazione, è possibile scegliere tra le opzioni seguenti:

1. Se si usa questa attività raramente, o pochi secondi non è rilevante per la compilazione, è possibile usare le attività di MSBuild 'inline':

   - Attività XAML (una regola di compilazione personalizzata)

     Per un esempio di una dichiarazione di attività Xaml, vedere `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*e per l'utilizzo, vedere `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets*.

   - [Attività del codice](../msbuild/msbuild-inline-tasks.md)

1. Se si desidera migliorare le prestazioni delle attività o sufficiente funzionalità più complesse, usare MSBuild in modalità regolare [scrittura di attività](../msbuild/task-writing.md) processo.

   Se non tutti gli input e output dello strumento sono racchiusi nella riga di comando dello strumento, come il `CL`, `MIDL`, e `RC` casi e se si desidera input automatico e rilevamento dei file di output e la creazione di file TLog, derivare l'attività dal `Microsoft.Build.CPPTasks.TrackedVCToolTask`classe. Al momento, mentre è presente la documentazione per la base [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) classe, non sono disponibili esempi o per i dettagli della documentazione di `TrackedVCToolTask` classe. Se ciò è particolarmente interessante, aggiungere la voce dell'utente a una richiesta sul [developercommunity.visualstudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="incremental-builds-and-up-to-date-checks"></a>Le compilazioni incrementali e controlli aggiornati

La compilazione incrementale MSBuild predefinito è destinato a uso `Inputs` e `Outputs` attributi. Se specificate, MSBuild chiama la destinazione solo se uno degli input ha un timestamp più recente rispetto a tutti gli output. Poiché i file di origine spesso includono o importano altri file e compilare strumenti producono output diversi a seconda delle opzioni dello strumento, è difficile specificare tutti i possibili input e output nelle destinazioni di MSBuild.

Per gestire questo problema, la compilazione C++ Usa una tecnica diversa per supportare le compilazioni incrementali. Quasi tutte le destinazioni non specificare input e output e di conseguenza, eseguire sempre durante la compilazione. Le attività di chiamata da destinazioni di scrivono informazioni su tutti i valori di input e output in *tlog* file TLog con estensione. File TLog vengono utilizzati per le compilazioni successive per verificare cosa è stato modificato e deve essere ricompilato e che cosa è aggiornata.

Per determinare tutti gli input e output, le attività degli strumenti nativi usano tracker.exe e il [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) classe fornita da MSBuild.

Microsoft.Build.CPPTasks.Common.dll definisce il `TrackedVCToolTask` classe base astratta pubblica. La maggior parte delle attività degli strumenti nativi sono derivata da questa classe.

## <a name="tlog-files"></a>file TLog

Esistono tre tipi di file TLog: *letto*, *scrivere*, e *della riga di comando*. File TLog di lettura e scrittura vengono usati per le compilazioni incrementali e per la verifica di aggiornamento nell'IDE. File TLog da riga di comando vengono utilizzati solo nelle compilazioni incrementali.

MSBuild fornisce queste classi helper per leggere e scrivere file TLog:

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

Il [FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) classe può essere utilizzata per accedere sia in lettura e scrittura file TLog e identificare gli input più recenti rispetto a output, o se non è presente un output. Viene usato nella verifica di aggiornamento.

File TLog da riga di comando contengono informazioni sulle righe di comando usate nella compilazione. Vengono usati solo per le compilazioni incrementali, i controlli non aggiornati, in modo che il formato interno è determinato dall'attività di MSBuild che li produce.

Se vengono creati file TLog da un'attività, è consigliabile usare queste classi helper per crearli. Tuttavia, poiché la verifica di aggiornamento predefinito a questo punto si basa esclusivamente sui file TLog, in alcuni casi è preferibile produzione degli stessi in una destinazione senza un'attività. È possibile scriverli usando le `WriteLinesToFile` attività. Vedere le `_WriteMasmTlogs` di destinazione `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets* come esempio.

### <a name="read-tlog-format"></a>Formato di tlog di lettura

*Lettura* file TLog (\*file TLog. Read.\*. TLog) contiene informazioni sui file di origine e le relative dipendenze.

Un accento circonflesso (**^**) all'inizio di una riga indica una o più origini. Origini che condividono le stesse dipendenze sono separate da una barra verticale (**\|**).

File di dipendenza vengono elencati dopo le origini, ognuno nella propria riga. Tutti i nomi file sono percorsi completi.

Si supponga ad esempio le origini del progetto si trovano nella *f:.\\testare\\ConsoleApplication1\\ConsoleApplication1*. Se il file di origine *Class1.cpp*, sono questi sono inclusi,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

l'oggetto *CL.read.1.tlog* file contiene il file di origine seguito dalle relative due dipendenze:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Non è necessario scrivere i nomi di file in lettere maiuscole, ma è utile per alcuni strumenti.

### <a name="write-tlog-format"></a>Formato di tlog di scrittura

*Scrivere* TLog (\*clausola. Write.\*. file tlog) connettere origini e output.

Un accento circonflesso (**^**) all'inizio di una riga indica una o più origini. Più origini sono separate da una barra verticale (**\|**).

I file di output compilati dalle origini dovrebbero essere elencati dopo le origini, ognuno nella propria riga. Tutti i nomi di file devono essere percorsi completi.

Ad esempio, per un progetto ConsoleApplication semplice con un file di origine aggiuntivi *Class1.cpp*, il *link.write.1.tlog* file può contenere:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Compilazione in fase di progettazione

Nell'IDE, con estensione vcxproj progetti usano un set di destinazioni di MSBuild per ottenere informazioni aggiuntive dal progetto e rigenerare i file di output. Alcune di queste destinazioni vengono usati solo nelle compilazioni in fase di progettazione, ma molti di essi vengono usati in entrambe le build regolari e compilazioni in fase di progettazione.

Per informazioni generali sulle compilazioni in fase di progettazione, vedere la documentazione CPS [compilazioni in fase di progettazione](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Questa documentazione è parzialmente applicabile solo ai progetti Visual C++.

Il `CompileDesignTime` e `Compile` destinazioni indicate in fase di progettazione si basa documentazione mai stata eseguita per i progetti con estensione vcxproj. I progetti di Visual C++ con estensione vcxproj usano diverse destinazioni in fase di progettazione per ottenere le informazioni di IntelliSense.

### <a name="design-time-targets-for-intellisense-information"></a>Destinazioni in fase di progettazione per le informazioni di IntelliSense

Sono definite le destinazioni in fase di progettazione usate nei progetti con estensione vcxproj `$(VCTargetsPath)` \\ *Microsoft.Cpp.DesignTime.targets*.

Il `GetClCommandLines` opzioni del compilatore per IntelliSense vengono raccolti nella destinazione:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` : in fase di progettazione solo l'inizializzazione di compilazione di destinazioni, necessari per la fase di progettazione. Tra le altre cose, queste destinazioni di disabilitare alcune delle funzionalità di compilazione normale per migliorare le prestazioni.

- `ComputeCompileInputsTargets` -un set di destinazioni che modifica le opzioni del compilatore e gli elementi. Queste destinazioni vengono eseguiti in fase di progettazione e regolare le compilazioni.

Le chiamate di destinazione di `CLCommandLine` attività per creare la riga di comando da utilizzare per IntelliSense. Malgrado il nome, anche in questo caso, può gestire non solo opzioni CL, ma anche le opzioni di Clang e gcc. Il tipo di opzioni del compilatore è controllato dal `ClangMode` proprietà.

Attualmente, la riga di comando prodotta dal `CLCommandLine` attività Usa sempre commutatori CL (anche in modalità Clang) perché sono più semplici per il motore di IntelliSense da analizzare.

Se si aggiunge una destinazione che viene eseguito prima della compilazione, regolare o fase di progettazione, assicurarsi non viene interrotto in fase di progettazione si basa o influire sulle prestazioni. Il modo più semplice per testare la destinazione è aprire un prompt dei comandi per gli sviluppatori ed eseguire questo comando:

> MSBuild /p:SolutionDir =*soluzione-directory-con-finali-barra rovesciata*; Configurazione = Debug; Piattaforma = Win32; BuildingInsideVisualStudio = true; DesignTimebuild = /t: true\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*vcxproj

Questo comando genera un log di creazione dettagliate *MSBuild*, che influisce sulle prestazioni per le destinazioni e attività di riepilogo alla fine.

Assicurarsi di usare `Condition ="'$(DesignTimeBuild)' != 'true'"` in tutte le operazioni che hanno un solo significato per le compilazioni normali e non per le compilazioni in fase di progettazione.

### <a name="design-time-targets-that-generate-sources"></a>Destinazioni in fase di progettazione che generano le origini

*Questa funzionalità è disabilitata per impostazione predefinita per i progetti Desktop native e non è attualmente supportata nei progetti memorizzato nella cache*.

Se `GeneratorTarget` i metadati sono definiti per un elemento del progetto, la destinazione viene eseguita automaticamente entrambi quando viene caricato il progetto e quando viene modificato il file di origine.

Ad esempio, per generare automaticamente i file cpp o h i file dal file con estensione XAML, il `$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\  *WindowsXaml*\\*v15.0*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets* file definiscono questi entità:

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

Per utilizzare `Task.HostObject` per ottenere il contenuto dei file di origine non sono stato salvato, le destinazioni e attività deve essere registrati come [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) per i progetti specificati in un pkgdef:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Estensibilità di progetto Visual C++ nell'IDE di Visual Studio

Il sistema di progetto Visual C++ si basa sul [sistema di progetto di Visual Studio](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)e Usa i relativi punti di estendibilità. Tuttavia, l'implementazione di gerarchia del progetto è specifico di Visual C++ e non basati su CPS, estendibilità gerarchia è possibile solo per gli elementi del progetto.

### <a name="project-property-pages"></a>Pagine delle proprietà del progetto

Per informazioni sulla progettazione generale, vedere [estendibilità della piattaforma - parte 1](https://blogs.msdn.microsoft.com/vsproject/2009/06/09/platform-extensibility-part-1/) e [estendibilità della piattaforma - parte 2](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/).

In altre parole, le pagine delle proprietà presenti il **proprietà progetto** finestra di dialogo per un progetto C++ sono definiti dal *regola* file. Un file di regole specifica un set di proprietà da visualizzare nella pagina delle proprietà e come e dove devono essere salvati nel progetto di file. File di regole sono file con estensione XML che usano il formato Xaml. Sono descritti i tipi usati per serializzarle [Microsoft.Build.Framework.XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes). Per altre informazioni sull'uso dei file di regole nei progetti, vedere [file di regole XML pagina delle proprietà](/cpp/ide/property-page-xml-files).

I file di regola devono essere aggiunti al `PropertyPageSchema` gruppo di elementi:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` metadati limitano la visibilità di regola, che viene controllata anche dal tipo di regola e può avere uno dei valori seguenti:

> `Project` | `File` | `PropertySheet`

CPS supporta altri valori per il tipo di contesto, ma non vengono usati nei progetti Visual C++.

Se la regola deve essere visibile in più di un contesto, usare i punti e virgola (**;**) per separare i valori di contesto, come illustrato di seguito:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Formato della regola e tipi principali

Il formato della regola è semplice, in modo che in questa sezione vengono descritti solo gli attributi che influiscono sul modo in cui la regola cerca nell'interfaccia utente.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

Il `PageTemplate` attributo definisce come la regola venga visualizzata nel **pagine delle proprietà** finestra di dialogo. L'attributo può avere uno dei valori seguenti:


| Attributo | Descrizione |
|------------| - |
| `generic` | Tutte le proprietà vengono visualizzate in un'unica pagina sotto le intestazioni di categoria<br/>La regola può essere visibile per la `Project` e `PropertySheet` contesti, ma non `File`.<br/><br/> Esempio: `$(VCTargetsPath)`\\*1033*\\*General* |
| `tool` | Le categorie vengono visualizzate come pagine secondarie.<br/>La regola può essere visibile in tutti i contesti: `Project`, `PropertySheet` e `File`.<br/>La regola è visibile nelle proprietà del progetto solo se il progetto contiene elementi con il `ItemType` definito in `Rule.DataSource`, a meno che il nome della regola è inclusa nel `ProjectTools` gruppo di elementi.<br/><br/>Esempio: `$(VCTargetsPath)`\\*1033*\\*clang.xml* |
| `debugger` | La pagina viene visualizzata come parte della pagina di debug.<br/>Le categorie vengono attualmente ignorate.<br/>Il nome della regola deve corrispondere l'oggetto di eseguire il Debug dell'utilità di avvio MEF `ExportDebugger` attributo.<br/><br/>Esempio: `$(VCTargetsPath)`\\*1033*\\*debugger\_locale\_windows.xml* |
| *custom* | Modello personalizzato. Il nome del modello deve corrispondere il `ExportPropertyPageUIFactoryProvider` attributo del `PropertyPageUIFactoryProvider` oggetto MEF. Visualizzare **Microsoft.VisualStudio.ProjectSystem.Designers.Properties.IPropertyPageUIFactoryProvider**.<br/><br/> Esempio: `$(VCTargetsPath)`\\*1033*\\*userMacros.xml* |

Se la regola usa uno dei modelli basati su griglia di proprietà, è possibile utilizzare questi punti di estendibilità per le relative proprietà:

- [Editor di valori di proprietà](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Provider di valori di enumerazione dinamica](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Estendere una regola

Se si desidera utilizzare una regola esistente, ma necessario aggiungere o rimuovere (che è, nascondere) solo alcune proprietà, è possibile creare un [regola estensioni](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Eseguire l'override di una regola

Si supponga il set di strumenti per usare la maggior parte delle regole predefinite di progetto, ma per sostituire uno solo o alcune di esse. Pronunciare, ad esempio, che si vuole solo modificare la regola di C/C++ per visualizzare le opzioni del compilatore diverse. È possibile fornire una nuova regola con lo stesso nome e nome visualizzato della regola esistente e includerlo nel `PropertyPageSchema` gruppo di elementi dopo l'importazione di destinazioni predefinite cpp. Solo una regola con un nome specificato viene utilizzata nel progetto e quella più recente inclusa nel `PropertyPageSchema` elemento wins gruppo.

#### <a name="project-items"></a>Elementi di progetto

Il *Projectitemsschema* file cpp definisce la `ContentType` e `ItemType` i valori per gli elementi che vengono considerati come elementi di progetto e definisce `FileExtension` gli elementi per determinare quale gruppo di elementi di un nuovo file viene aggiunto a.

Il file ProjectItemsSchema predefinito si trova `$(VCTargetsPath)` \\ *1033*\\*Projectitemsschema*. Per estenderlo, è necessario creare un file di schema con un nuovo nome, ad esempio *MyProjectItemsSchema.xml*:

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

Quindi nel file di destinazioni, aggiungere:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Esempio: `$(VCTargetsPath)`\\*BuildCustomizations*\\*masm.xml*

### <a name="debuggers"></a>Debugger

Il servizio di Debug in Visual Studio supporta l'estendibilità per il motore di Debug. Per altre informazioni, vedere gli esempi seguenti:

- [MIEngine, progetto open source che supporta il debug lldb](https://github.com/Microsoft/MIEngine)

- [Esempio di Visual Studio debug motore](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Per specificare altre proprietà e i motori di Debug per la sessione di debug, è necessario implementare una [eseguire il Debug dell'utilità di avvio](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) componente MEF e aggiungere un `debugger` regola. Per un esempio, vedere la `$(VCTargetsPath)` \\1033\\debugger\_locale\_windows.xml file.

### <a name="deploy"></a>Distribuzione

i progetti con estensione vcxproj usare per estendere il sistema di progetto di Visual Studio [distribuire provider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Compilare una verifica di aggiornamento

Per impostazione predefinita, la verifica di aggiornamento di compilazione richiede la lettura dei file TLog di tlog e scrittura deve essere creato nel `$(TlogLocation)` cartella durante la compilazione per tutti gli input di compilazione e gli output.

Per usare un controllo di aggiornamento personalizzato:

1. Disabilitare la verifica di aggiornamento predefinito aggiungendo la `NoVCDefaultBuildUpToDateCheckProvider` capacità nel *Toolset.targets* file:

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Implementare il proprio [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Aggiornamento del progetto

### <a name="default-vcxproj-project-upgrader"></a>Upgrader di progetto vcxproj predefinito

Le modifiche di upgrader progetto vcxproj predefinito di `PlatformToolset`, `ApplicationTypeRevision`, versione e .net framework di set di strumenti di MSBuild. Gli ultimi due sono sempre modificati in Visual Studio versione predefiniti, ma `PlatformToolset` e `ApplicationTypeRevision` può essere controllato dalla proprietà speciali di MSBuild.

L'upgrader Usa questi criteri per decidere se un progetto può essere aggiornato o non:

1. Per i progetti che definiscono `ApplicationType` e `ApplicationTypeRevision`, è presente una cartella con un numero di revisione superiore rispetto a quella corrente.

1. La proprietà `_UpgradePlatformToolsetFor_<safe_toolset_name>` è definito per il set di strumenti corrente e il relativo valore non è uguale al set di strumenti corrente.

   In questi nomi di proprietà,  *\<safe_toolset_name >* rappresenta il nome del set di strumenti con tutti i caratteri non alfanumerici sostituiti da un carattere di sottolineatura (**\_**).

Quando un progetto può essere aggiornato, partecipi *soluzione ridestinazione*. Per altre informazioni, vedere [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Se si desidera per decorare i nomi dei progetti **Esplora soluzioni** quando i progetti usano un set di strumenti specifico, definire un `_PlatformToolsetShortNameFor_<safe_toolset_name>` proprietà.

Per esempi relativi `_UpgradePlatformToolsetFor_<safe_toolset_name>` e `_PlatformToolsetShortNameFor_<safe_toolset_name>` definizioni delle proprietà, vedere la *Microsoft.Cpp.Default.props* file. Per esempi di utilizzo, vedere la `$(VCTargetPath)` \\ *Microsoft.Cpp.Platform.targets* file.

### <a name="custom-project-upgrader"></a>Upgrader personalizzato progetto

Per usare un oggetto upgrader progetto personalizzato, implementare un componente MEF, come illustrato di seguito:

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

Il codice è possibile importare e chiamare il metodo predefinito con estensione vcxproj upgrader oggetto:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` è definito in *Microsoft.VisualStudio.ProjectSystem.VS.dll* ed è simile a `IVsRetargetProjectAsync`.

Definire il `VCProjectUpgraderObjectName` proprietà per indicare al sistema di progetto per utilizzare l'oggetto upgrader personalizzato:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Disabilitare l'aggiornamento di progetto

Per disabilitare gli aggiornamenti di progetti, usare un `NoUpgrade` valore:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>La cache del progetto ed estendibilità

Per migliorare le prestazioni quando si lavora con soluzioni di grandi dimensioni C++ in Visual Studio 2017, il [cache del progetto](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-solution-load-with-vs-15/) è stata introdotta. Viene implementato come un database SQLite popolata con i dati del progetto e quindi usato per caricare i progetti senza caricare i progetti MSBuild o CPS in memoria.

Perché non sono presenti oggetti CPS presenti per i progetti con estensione vcxproj caricati dalla cache, i componenti MEF dell'estensione di importazione `UnconfiguredProject` o `ConfiguredProject` non può essere creato. Per supportare l'estendibilità, la cache del progetto non viene usata quando Visual Studio rileva se un progetto Usa (o è probabile che vengano utilizzati) estensioni MEF.

Questi tipi di progetto sono sempre completamente caricati e hanno CPS oggetti in memoria, in modo che tutte le estensioni MEF vengono create per loro:

- Progetti di avvio

- I progetti che hanno un upgrader personalizzato progetto, vale a dire, definire un `VCProjectUpgraderObjectName` proprietà

- I progetti destinati a non Windows Desktop, vale a dire, definiscono un' `ApplicationType` proprietà

- Condiviso (.vcxitems) i progetti di elementi e tutti i progetti che fanno riferimento a essi da importare progetti .vcxitems.

Se nessuna di queste condizioni vengono rilevata, viene creata una cache di progetto. La cache include tutti i dati dal progetto di MSBuild necessarie per rispondere `get` esegue una query sul `VCProjectEngine` interfacce. Ciò significa che tutte le modifiche apportate alla proprietà di MSBuild e a livello di file di destinazioni eseguita da un'estensione dovrebbe funzionare solo nei progetti caricati dalla cache.

## <a name="shipping-your-extension"></a>L'estensione di spedizione

Per informazioni su come creare i file VSIX, vedere [spedizione di estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Per informazioni su come aggiungere file a percorsi di installazione speciale, ad esempio, per aggiungere i file sotto `$(VCTargetsPath)`, vedere [installazione all'esterno della cartella delle estensioni](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Risorse aggiuntive

Il sistema di compilazione Microsoft ([MSBuild](../msbuild/msbuild.md)) fornisce il motore di compilazione e il formato estensibile basato su XML per i file di progetto. È necessario avere familiarità con basic [concetti relativi a MSBuild](../msbuild/msbuild-concepts.md) e con le procedure [MSBuild per Visual C++](/cpp/build/msbuild-visual-cpp-overview) sistema del progetto funziona per estendere Visual C++.

Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) fornisce l'estensione di API utilizzate da CPS e il sistema di progetto Visual C++. Per una panoramica dell'utilizzo di MEF da CPS, vedere [CPS e MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) nel [VSProjectSystem Panoramica di MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

È possibile personalizzare il sistema di compilazione esistente per aggiungere istruzioni di compilazione o nuovi tipi di file. Per altre informazioni, vedere [Cenni preliminari su MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp-overview) e [funziona con le proprietà del progetto](/cpp/ide/working-with-project-properties).
