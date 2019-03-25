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
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: bd0c5510c754043a0a55b305c671ce9487cabb49
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070433"
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