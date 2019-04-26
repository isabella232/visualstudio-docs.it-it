---
title: Classe TrackedVCToolTask | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 4a4044416131a27ca313d10d02404094c5f5e219
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62938869"
---
# <a name="trackedvctooltask-base-class"></a>Classe di base TrackedVCToolTask

Molte attività ereditano dalla classe <xref:Microsoft.Build.Utilities.Task> e dalla classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Questa classe aggiunge diversi parametri alle attività che derivano da [VCToolTask](../msbuild/vctooltask-base-class.md). Questi parametri sono elencati in questo documento.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri della classe di base **TrackedVCToolTask**.

|Parametro|Description|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Parametro **bool** facoltativo.|
|**EnableExecuteTool**|Parametro **bool** facoltativo.|
|**ExcludedInputPaths**|Parametro **ITaskItem[]** facoltativo.|
|**MinimalRebuildFromTracking**|Parametro **bool** facoltativo.|
|**PathOverride**|Parametro **string** facoltativo.|
|**PostBuildTrackingCleanup**|Parametro **bool** facoltativo.|
|**RootSource**|Parametro **string** facoltativo.|
|**SkippedExecution**|Parametro di output **bool** facoltativo.|
|**SourcesCompiled**|Parametro di output **ITaskItem[]** facoltativo.|
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

[Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)<br/>
[Attività](../msbuild/msbuild-tasks.md)