---
title: Attività di MSBuild specifiche di C++ | Microsoft Docs
description: Vedere le attività MSBuild disponibili quando è installato C++, usato da MSBuild per la compilazione di codice C++.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: b1d1a40c9e173ec6dd7cf07e0af0ca68f58efbb0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049033"
---
# <a name="msbuild-tasks-specific-to-c"></a>Attività di MSBuild specifiche di C++

Le attività forniscono il codice che viene eseguito durante il processo di compilazione. Quando viene installato C++, sono disponibili le attività seguenti, oltre a quelle installate con MSBuild. Per ulteriori informazioni, vedere [Cenni preliminari su MSBuild (C++)](/cpp/build/msbuild-visual-cpp-overview).

 Ogni attività dispone di parametri propri e anche dei parametri seguenti.

| Parametro | Descrizione |
|-------------------| - |
| `Condition` | Parametro `String` facoltativo.<br /><br /> `Boolean`Espressione utilizzata dal motore MSBuild per determinare se questa attività verrà eseguita. Per informazioni sulle condizioni supportate da MSBuild, vedere [condizioni](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Parametro facoltativo. Può contenere uno dei valori seguenti:<br /><br /> -   **WarnAndContinue** o **true** . Quando un'attività ha esito negativo, l'esecuzione delle attività successive nell'elemento [Target](../msbuild/target-element-msbuild.md) e della compilazione continua e tutti gli errori delle attività vengono considerati avvisi.<br />-   **ErrorAndContinue** . Quando un'attività ha esito negativo, l'esecuzione delle attività successive nell'elemento `Target` e della compilazione continua e tutti gli errori delle attività vengono considerati errori.<br />-   **ErrorAndStop** o **false** (impostazione predefinita). Quando un'attività ha esito negativo, le attività rimanenti nell'elemento `Target` e la compilazione non vengono eseguite e l'intero elemento `Target` e la compilazione vengono considerati come non riusciti.<br /><br /> Le versioni di .NET Framework precedenti alla 4.5 supportano solo i valori `true` e `false`.<br /><br /> Per altre informazioni, vedere [procedura: ignorare gli errori nelle attività](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Attività BscMake](../msbuild/bscmake-task.md)|Esegue il wrapping dello strumento Microsoft Browse Information Maintenance Utility ( *bscmake.exe* ).|
|[attività CL](../msbuild/cl-task.md)|Esegue il wrapping dello strumento compilatore C++ ( *cl.exe* ).|
|[Attività CPPClean](../msbuild/cppclean-task.md)|Elimina i file temporanei creati da MSBuild quando viene compilato un progetto C++.|
|[Attività ClangCompile](../msbuild/clangcompile-task.md)|Esegue il wrapping dello strumento compilatore C++ ( *clang.exe* ).|
|[Attività CustomBuild](../msbuild/custombuild-task.md)|Esegue il wrapping dello strumento compilatore C++ ( *cmd.exe* ).|
|[Attività FXC](../msbuild/fxc-task.md)|Usare i compilatori di shader HLSL nel processo di compilazione.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Legge i tlog precedenti, scrive nuovi tlog e restituisce set di elementi che non sono aggiornati. (attività di supporto)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Ottiene il nome del file di output per cl e altri strumenti, che consentono di specificare solo la directory di output o il nome di file completo o nulla. (attività di supporto)|
|[LIB (attività)](../msbuild/lib-task.md)|Esegue il wrapping dello strumento di gestione librerie a 32 bit di Microsoft ( *lib.exe* ).|
|[Link (attività)](../msbuild/link-task.md)|Esegue il wrapping dello strumento linker di C++ ( *link.exe* ).|
|[MIDL (attività)](../msbuild/midl-task.md)|Esegue il wrapping dello strumento compilatore Microsoft Interface Definition Language (MIDL) ( *midl.exe* ).|
|[attività MT](../msbuild/mt-task.md)|Esegue il wrapping dello strumento Manifesto Microsoft ( *mt.exe* ).|
|[Attività MultiToolTask](../msbuild/multitooltask-task.md)|Nessuna descrizione.|
|[Attività ParallelCustomBuild](../msbuild/parallelcustombuild-task.md)|Eseguire istanze parallele dell'[attività CustomBuild](../msbuild/custombuild-task.md).|
|[RC (attività)](../msbuild/rc-task.md)|Esegue il wrapping dello strumento compilatore di risorse di Microsoft Windows ( *rc.exe* ).|
|[Attività SetEnv](../msbuild/setenv-task.md)|Imposta o elimina il valore di una variabile di ambiente specificata.|
|[Classe di base TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)|Eredita da [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[attività VCMessage](../msbuild/vcmessage-task.md)|Registra i messaggi di avviso e i messaggi di errore durante una compilazione. (Non estendibile. Solo per uso interno).|
|[Classe di base VCToolTask](../msbuild/vctooltask-base-class.md)|Eredita da [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[attività XDCMake](../msbuild/xdcmake-task.md)|Esegue il wrapping dello strumento di documentazione XML ( *xdcmake.exe* ), che unisce i file di commento del documento XML (con *estensione xdc* ) in un file con estensione *XML* .|
|[XSD (attività)](../msbuild/xsd-task.md)|Esegue il wrapping dello strumento XML Schema Definition ( *xsd.exe* ), che genera file di schema o di classe da un'origine. *Vedere la nota che segue.*|
|[Riferimenti a MSBuild](../msbuild/msbuild-reference.md)|Descrive gli elementi del sistema MSBuild.|
|[Attività](../msbuild/msbuild-tasks.md)|Descrive le attività, che sono unità di codice che possono essere combinate per produrre una compilazione.|
|[Scrittura di attività](../msbuild/task-writing.md)|Descrive come creare un'attività.|

> [!NOTE]
> A partire da Visual Studio 2017, il supporto dei progetti C++ per *xsd.exe* è deprecato. È comunque possibile usare le API **Microsoft.VisualC.CppCodeProvider** aggiungendo manualmente *CppCodeProvider.dll* alla Global Assembly Cache.
