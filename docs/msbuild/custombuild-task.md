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
- MSBuild (Visual C++), CustomBuild task
- CustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 04f33f3852f051e1f492cb2b6dca44fcdb260e11
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/05/2019
ms.locfileid: "67587013"
---
# <a name="custombuild-task"></a>Attività CustomBuild

Esegue il wrapping dello strumento del compilatore Visual C++, cmd.exe. Questa classe deriva da [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), ma non usa il rilevamento file per individuare le dipendenze di file. Affinché la compilazione incrementale funzioni correttamente, tutte le dipendenze devono essere specificate esplicitamente come AdditionalDependencies.

## <a name="parameters"></a>Parametri

La tabella seguente descrive i parametri dell'attività **CustomBuild**.

|Parametro|DESCRIZIONE|
|---------------|-----------------|
|**BuildSuffix**|Parametro **string** facoltativo.|
|**Sources**|Parametro **ITaskItem[]** obbligatorio.|
|**TrackerLogDirectory**|Parametro **string** facoltativo.|

## <a name="see-also"></a>Vedere anche

[Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)
