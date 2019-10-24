---
title: Attività di MSBuild specifiche C++ di | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d6ea400d7473fae27ac4b17d9e3692748db549f3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748064"
---
# <a name="msbuild-tasks-specific-to-c"></a>Attività di MSBuild specifiche diC++
Le attività forniscono il codice che viene eseguito durante il processo di compilazione. Quando C++ è installato, sono disponibili le attività seguenti, oltre a quelle installate con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Per ulteriori informazioni, vedere [Cenni preliminari su MSBuildC++()](/cpp/build/msbuild-visual-cpp-overview).

 Ogni attività dispone di parametri propri e anche dei parametri seguenti.

| Parametro | Descrizione |
|-------------------| - |
| `Condition` | Parametro `String` facoltativo.<br /><br /> Espressione `Boolean` usata dal motore di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per determinare se l'attività verrà eseguita. Per altre informazioni sulle condizioni supportate da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], vedere [Condizioni](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Parametro facoltativo. Può contenere uno dei valori seguenti:<br /><br /> -   **WarnAndContinue** o **true**. Quando un'attività ha esito negativo, l'esecuzione delle attività successive nell'elemento [Target](../msbuild/target-element-msbuild.md) e della compilazione continua e tutti gli errori delle attività vengono considerati avvisi.<br />-   **ErrorAndContinue**. Quando un'attività ha esito negativo, l'esecuzione delle attività successive nell'elemento `Target` e della compilazione continua e tutti gli errori delle attività vengono considerati errori.<br />-   **ErrorAndStop** o **false** (impostazione predefinita). Quando un'attività ha esito negativo, le attività rimanenti nell'elemento `Target` e la compilazione non vengono eseguite e l'intero elemento `Target` e la compilazione vengono considerati come non riusciti.<br /><br /> Le versioni di .NET Framework precedenti alla 4.5 supportano solo i valori `true` e `false`.<br /><br /> Per altre informazioni, vedere [Procedura: Ignorare gli errori nelle attività](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Attività BscMake](../msbuild/bscmake-task.md)|Esegue il wrapping dello strumento Microsoft Browse Information Maintenance Utility (*bscmake.exe*).|
|[Attività CL](../msbuild/cl-task.md)|Esegue il wrapping C++ dello strumento del compilatore (*CL. exe*).|
|[Attività CPPClean](../msbuild/cppclean-task.md)|Elimina i file temporanei creati da MSBuild durante C++ la compilazione di un progetto.|
|[Attività ClangCompile](../msbuild/clangcompile-task.md)|Esegue il wrapping C++ dello strumento del compilatore (*Clang. exe*).|
|[Attività CustomBuild](../msbuild/custombuild-task.md)|Esegue il wrapping C++ dello strumento del compilatore (*cmd. exe*).|
|[Attività FXC](../msbuild/fxc-task.md)|Usare i compilatori di shader HLSL nel processo di compilazione.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Legge i tlog precedenti, scrive nuovi tlog e restituisce set di elementi che non sono aggiornati. (attività di supporto)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Ottiene il nome del file di output per cl e altri strumenti, che consentono di specificare solo la directory di output o il nome di file completo o nulla. (attività di supporto)|
|[Attività LIB](../msbuild/lib-task.md)|Esegue il wrapping dello strumento di gestione librerie Microsoft a 32 bit, *lib.exe*.|
|[Attività Link](../msbuild/link-task.md)|Esegue il wrapping C++ dello strumento Linker (*link. exe*).|
|[Attività MIDL](../msbuild/midl-task.md)|Esegue il wrapping dello strumento compilatore MIDL (Microsoft Interface Definition Language), *midl.exe*.|
|[Attività MT](../msbuild/mt-task.md)|Esegue il wrapping dello strumento manifesto Microsoft, *mt.exe*.|
|[Attività MultiToolTask](../msbuild/multitooltask-task.md)|Nessuna descrizione.|
|[Attività ParallelCustomBuild](../msbuild/parallelcustombuild-task.md)|Eseguire istanze parallele dell'[attività CustomBuild](../msbuild/custombuild-task.md).|
|[Attività RC](../msbuild/rc-task.md)|Esegue il wrapping dello strumento Compilatore di risorse di Microsoft Windows, *rc.exe*.|
|[Attività SetEnv](../msbuild/setenv-task.md)|Imposta o elimina il valore di una variabile di ambiente specificata.|
|[Classe di base TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)|Eredita da [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[Attività VCMessage](../msbuild/vcmessage-task.md)|Registra i messaggi di avviso e i messaggi di errore durante una compilazione. (Non estendibile. Solo per uso interno).|
|[Classe di base VCToolTask](../msbuild/vctooltask-base-class.md)|Eredita da [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[Attività XDCMake](../msbuild/xdcmake-task.md)|Esegue il wrapping dello strumento Documentazione XML (*xdcmake.exe*) che unisce i file di commento (con estensione *xdc*) del documento XML in un file con estensione *xml*.|
|[Attività XSD](../msbuild/xsd-task.md)|Esegue il wrapping dello strumento XML Schema Definition (*xsd.exe*), che genera file di schema o di classe da un'origine. *Vedere la nota seguente.*|
|[Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)|Descrive gli elementi del sistema MSBuild.|
|[Attività](../msbuild/msbuild-tasks.md)|Descrive le attività, che sono unità di codice che possono essere combinate per produrre una compilazione.|
|[Scrittura di attività](../msbuild/task-writing.md)|Descrive come creare un'attività.|

> [!NOTE]
> A partire da Visual Studio 2017, il supporto dei progetti C++ per *xsd.exe* è deprecato. È comunque possibile usare le API **Microsoft.VisualC.CppCodeProvider** aggiungendo manualmente *CppCodeProvider.dll* alla Global Assembly Cache.