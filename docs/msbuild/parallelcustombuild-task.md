---
title: Attività ParallelCustomBuild | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 54623ab1c58d85de55c5b8a24384bf0be46f1a61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963754"
---
# <a name="parallelcustombuild-task"></a>Attività ParallelCustomBuild

Eseguire istanze parallele dell'[attività CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **ParallelCustomBuild**.

|Parametro|Description|
|---------------|-----------------|
|**BreakOnFirstFailure**|Parametro **bool** facoltativo.|
|**MaxItemsInBatch**|Parametro **int** facoltativo.|
|**MaxProcesses**|Parametro **int** facoltativo.|
|**Sources**|Parametro **ITaskItem[]** obbligatorio.|

## <a name="see-also"></a>Vedere anche

[Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)