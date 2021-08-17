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
ms.openlocfilehash: 921a79c78dbec3df58a78d7dd41011a60d825fd1961ee7a3233e28c5bafec122
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121443160"
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