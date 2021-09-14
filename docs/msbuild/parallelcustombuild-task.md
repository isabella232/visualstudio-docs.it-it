---
title: Attività ParallelCustomBuild | Microsoft Docs
description: Informazioni su MSBuild'attività ParallelCustomBuild per eseguire istanze parallele dell'attività CustomBuild.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628398"
---
# <a name="parallelcustombuild-task"></a>Attività ParallelCustomBuild

Eseguire istanze parallele dell'[attività CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **ParallelCustomBuild**.

|Parametro|Descrizione|
|---------------|-----------------|
|**BreakOnFirstFailure**|Parametro **bool** facoltativo.|
|**MaxItemsInBatch**|Parametro **int** facoltativo.|
|**Maxprocesses**|Parametro **int** facoltativo.|
|**recenti**|Parametro **ITaskItem[]** obbligatorio.|

## <a name="see-also"></a>Vedi anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)