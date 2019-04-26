---
title: Attività MultiToolTask | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.multitooltask
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), MultiToolTask task
- MultiToolTask task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: a16a61c06bf80bef3fbb78f155cd8b41905a8d72
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963910"
---
# <a name="multitooltask-task"></a>Attività MultiToolTask

Nessuna descrizione.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **MultiToolTask**.

|Parametro|Description|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|Parametro **string[]** facoltativo.|
|**SemaphoreProcCount**|Parametro **string** facoltativo.|
|**SchedulerFunction**|Parametro **string** facoltativo.|
|**SchedulerVerbose**|Parametro **bool** facoltativo.|
|**Sources**|Parametro **ITaskItem[]** obbligatorio.|
|**TaskAssemblyName**|Parametro **string** facoltativo.|
|**TaskName**|Parametro **string** obbligatorio.|
|**TrackerLogDirectory**|Parametro **string** obbligatorio.|

## <a name="see-also"></a>Vedere anche

[Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)