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
- MSBuild (C++), MultiToolTask task
- MultiToolTask task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 137fb53a46c3fa31a69602906ef53d2f65e25c4b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747238"
---
# <a name="multitooltask-task"></a>Attività MultiToolTask

Nessuna descrizione.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **MultiToolTask**.

|Parametro|Descrizione|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|Parametro **string[]** facoltativo.|
|**SemaphoreProcCount**|Parametro **string** facoltativo.|
|**SchedulerFunction**|Parametro **string** facoltativo.|
|**SchedulerVerbose**|Parametro **bool** facoltativo.|
|**Sources**|Parametro **ITaskItem []** obbligatorio.|
|**TaskAssemblyName**|Parametro **string** facoltativo.|
|**TaskName**|Parametro **string** obbligatorio.|
|**TrackerLogDirectory**|Parametro **string** obbligatorio.|

## <a name="see-also"></a>Vedere anche

[Riferimento alle attività](../msbuild/msbuild-task-reference.md)