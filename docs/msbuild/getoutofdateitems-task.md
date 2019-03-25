---
title: Attività GetOutOfDateItems | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutofdateitems
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 668dddcd0854869c9ede7bf96c092d415f41dd17
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070407"
---
# <a name="getoutofdateitems-task"></a>Attività GetOutOfDateItems

Attività di supporto che legge i tlog precedenti, scrive nuovi tlog e restituisce set di elementi che non sono aggiornati.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **GetOutOfDateItems**.

|Parametro|Description|
|---------------|-----------------|
|**CheckForInterdependencies**|Parametro **bool** facoltativo.|
|**CommandMetadataName**|Parametro **string** facoltativo.|
|**DependenciesMetadataName**|Parametro **string** facoltativo.|
|**HasInterdependencies**|Parametro di output **bool** facoltativo.|
|**OutOfDateSources**|Parametro di output **ITaskItem[]** facoltativo.|
|**OutputsMetadataName**|Parametro **string** obbligatorio.|
|**Sources**|Parametro **ITaskItem[]** facoltativo.|
|**TLogDirectory**|Parametro **string** obbligatorio.|
|**TLogNamePrefix**|Parametro **string** obbligatorio.|

## <a name="see-also"></a>Vedere anche

[Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)