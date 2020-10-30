---
title: Attività ParallelCustomBuild | Microsoft Docs
description: Informazioni su come MSBuild usa l'attività ParallelCustomBuild per eseguire istanze parallele dell'attività CustomBuild.
ms.custom: SEO-VS-2020
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
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: f4491d0a5e9c9d3a2554bd32211fd1fa8f7be2d2
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048900"
---
# <a name="parallelcustombuild-task"></a>Attività ParallelCustomBuild

Eseguire istanze parallele dell'[attività CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **ParallelCustomBuild** .

|Parametro|Descrizione|
|---------------|-----------------|
|**BreakOnFirstFailure**|Parametro **bool** facoltativo.|
|**MaxItemsInBatch**|Parametro **int** facoltativo.|
|**MaxProcesses**|Parametro **int** facoltativo.|
|**recenti**|Parametro **ITaskItem[]** obbligatorio.|

## <a name="see-also"></a>Vedi anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)