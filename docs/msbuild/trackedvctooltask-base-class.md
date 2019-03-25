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
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 92d12e08f374efd306589d9d50f840a8d36f5b5a
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070460"
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