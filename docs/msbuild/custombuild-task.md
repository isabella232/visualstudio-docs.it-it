---
title: Attività CustomBuild | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d95b6e7d4197487adc13050572ac31310701c759
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595345"
---
# <a name="custombuild-task"></a>Attività CustomBuild

Esegue il wrapping dello strumento del compilatore di Microsoft C, cmd.exe. Questa classe deriva da [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), ma non usa il rilevamento file per individuare le dipendenze di file. Affinché la compilazione incrementale funzioni correttamente, tutte le dipendenze devono essere specificate esplicitamente come AdditionalDependencies.

## <a name="parameters"></a>Parametri

La tabella seguente descrive i parametri dell'attività **CustomBuild**.

|Parametro|Descrizione|
|---------------|-----------------|
|**BuildSuffix**|Parametro **stringa** facoltativo.|
|**recenti**|Parametro **ITaskItem[]** obbligatorio.|
|**TrackerLogDirectory**|Parametro **stringa** facoltativo.|

## <a name="see-also"></a>Vedere anche

[Riferimento alle attività](../msbuild/msbuild-task-reference.md)
