---
title: Attività MultiToolTask | Microsoft Docs
description: Accedere a una tabella che descrive i parametri obbligatori e facoltativi dell'attività MultiToolTask di MSBuild.
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
ms.openlocfilehash: 6d76aa3762b254ee35ada1e4e81fe857f509a4e5
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048979"
---
# <a name="multitooltask-task"></a>Attività MultiToolTask

Nessuna descrizione.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **MultiToolTask** .

|Parametro|Descrizione|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|Parametro **string[]** facoltativo.|
|**SemaphoreProcCount**|Parametro **stringa** facoltativo.|
|**SchedulerFunction**|Parametro **stringa** facoltativo.|
|**SchedulerVerbose**|Parametro **bool** facoltativo.|
|**recenti**|Parametro **ITaskItem[]** obbligatorio.|
|**TaskAssemblyName**|Parametro **stringa** facoltativo.|
|**TaskName**|Parametro di **stringa** obbligatorio.|
|**TrackerLogDirectory**|Parametro di **stringa** obbligatorio.|

## <a name="see-also"></a>Vedi anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
