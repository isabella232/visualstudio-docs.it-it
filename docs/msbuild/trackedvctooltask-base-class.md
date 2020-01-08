---
title: Classe TrackedVCToolTask | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8a4272f7800e0532c0674fe7117e839cb16557d5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594929"
---
# <a name="trackedvctooltask-base-class"></a>Classe di base TrackedVCToolTask

Molte attività ereditano dalla classe <xref:Microsoft.Build.Utilities.Task> e dalla classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Questa classe aggiunge diversi parametri alle attività che derivano da [VCToolTask](../msbuild/vctooltask-base-class.md). Questi parametri sono elencati in questo documento.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri della classe di base **TrackedVCToolTask**.

|Parametro|Descrizione|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Parametro **bool** facoltativo.|
|**EnableExecuteTool**|Parametro **bool** facoltativo.|
|**ExcludedInputPaths**|Parametro **ITaskItem[]** facoltativo.|
|**MinimalRebuildFromTracking**|Parametro **bool** facoltativo.|
|**PathOverride**|Parametro **string** facoltativo.|
|**PostBuildTrackingCleanup**|Parametro **bool** facoltativo.|
|**RootSource**|Parametro **string** facoltativo.|
|**SkippedExecution**|Parametro di output **bool** facoltativo.|
|**SourcesCompiled**|Parametro di output facoltativo **ITaskItem[]** .|
|**TLogCommandFile**|Parametro **ITaskItem** facoltativo.|
|**TLogReadFiles**|Parametro **ITaskItem[]** facoltativo.|
|**TLogWriteFiles**|Parametro **ITaskItem[]** facoltativo.|
|**ToolArchitecture**|Parametro **string** facoltativo.|
|**TrackCommandLines**|Parametro **bool** facoltativo.|
|**TrackFileAccess**|Parametro **bool** facoltativo.|
|**TrackedInputFilesToIgnore**|Parametro **ITaskItem[]** facoltativo.|
|**TrackedOutputFilesToIgnore**|Parametro **ITaskItem[]** facoltativo.|
|**TrackerFrameworkPath**|Parametro **string** facoltativo.|
|**TrackerSdkPath**|Parametro **string** facoltativo.|

## <a name="see-also"></a>Vedere anche

[Riferimento alle attività](../msbuild/msbuild-task-reference.md)<br/>
[Attività](../msbuild/msbuild-tasks.md)
