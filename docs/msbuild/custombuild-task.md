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
ms.openlocfilehash: 6d466dec85a0bdf242120ef5e88a0d5f5d2ac48e
ms.sourcegitcommit: 0ef51e3517436a85cfb85bf492722d566ce602c4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934511"
---
# <a name="custombuild-task"></a>Attività CustomBuild

Esegue il wrapping dello strumento del compilatore Visual C++, cmd.exe. Questa classe deriva da [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), ma non usa il rilevamento file per individuare le dipendenze di file. Affinché la compilazione incrementale funzioni correttamente, tutte le dipendenze devono essere specificate esplicitamente come AdditionalDependencies.


## <a name="parameters"></a>Parametri

La tabella seguente descrive i parametri dell'attività **CustomBuild**.

|Parametro|Description|
|---------------|-----------------|
|**BuildSuffix**|Parametro **string** facoltativo.|
|**Sources**|Parametro **ITaskItem[]** obbligatorio.|
|**TrackerLogDirectory**|Parametro **string** facoltativo.|

## <a name="see-also"></a>Vedere anche

[Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)
