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
- MSBuild (C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: c6ea14e61eb2d62f3fc9ccdac3a17010ccc9194f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747229"
---
# <a name="parallelcustombuild-task"></a>Attività ParallelCustomBuild

Eseguire istanze parallele dell'[attività CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **ParallelCustomBuild**.

|Parametro|Descrizione|
|---------------|-----------------|
|**BreakOnFirstFailure**|Parametro **bool** facoltativo.|
|**MaxItemsInBatch**|Parametro **int** facoltativo.|
|**MaxProcesses**|Parametro **int** facoltativo.|
|**Sources**|Parametro **ITaskItem []** obbligatorio.|

## <a name="see-also"></a>Vedere anche

[Riferimento alle attività](../msbuild/msbuild-task-reference.md)