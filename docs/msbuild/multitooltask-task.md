---
title: Attività MultiToolTask | Microsoft Docs
description: Accedere a una tabella che descrive i parametri obbligatori e facoltativi dell'MSBuild MultiToolTask.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4b8fc1a20a1019981a1412344bdf3f6bdf0ad2d2f799ee811cd15ad7e422d126
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397332"
---
# <a name="multitooltask-task"></a>Attività MultiToolTask

Nessuna descrizione.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **MultiToolTask**.

|Parametro|Descrizione|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|Parametro **string[]** facoltativo.|
|**SemaphoreProcCount**|Parametro **di stringa** facoltativo.|
|**SchedulerFunction**|Parametro **di stringa** facoltativo.|
|**SchedulerVerbose**|Parametro **bool** facoltativo.|
|**recenti**|Parametro **ITaskItem[]** obbligatorio.|
|**TaskAssemblyName**|Parametro **di stringa** facoltativo.|
|**TaskName**|Parametro **di stringa** obbligatorio.|
|**TrackerLogDirectory**|Parametro **di stringa** obbligatorio.|

## <a name="see-also"></a>Vedi anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
