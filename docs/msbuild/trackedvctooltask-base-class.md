---
title: Classe TrackedVCToolTask | Microsoft Docs
description: Informazioni sui parametri aggiunti dalla classe di base TrackedVCToolTask alle attività che ereditano da essa.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 01b55e0ad88cb520078479217306bac948e6cd60
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625488"
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
|**PathOverride**|Parametro **di stringa** facoltativo.|
|**PostBuildTrackingCleanup**|Parametro **bool** facoltativo.|
|**RootSource**|Parametro **di stringa** facoltativo.|
|**SkippedExecution**|Parametro di output **bool** facoltativo.|
|**SourcesCompiled**|Parametro di output facoltativo **ITaskItem[]**.|
|**TLogCommandFile**|Parametro **ITaskItem** facoltativo.|
|**TLogReadFiles**|Parametro **ITaskItem[]** facoltativo.|
|**TLogWriteFiles**|Parametro **ITaskItem[]** facoltativo.|
|**ToolArchitecture**|Parametro **di stringa** facoltativo.|
|**TrackCommandLines**|Parametro **bool** facoltativo.|
|**TrackFileAccess**|Parametro **bool** facoltativo.|
|**TrackedInputFilesToIgnore**|Parametro **ITaskItem[]** facoltativo.|
|**TrackedOutputFilesToIgnore**|Parametro **ITaskItem[]** facoltativo.|
|**TrackerFrameworkPath**|Parametro **di stringa** facoltativo.|
|**TrackerSdkPath**|Parametro **di stringa** facoltativo.|

## <a name="see-also"></a>Vedi anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)<br/>
[Attività](../msbuild/msbuild-tasks.md)
