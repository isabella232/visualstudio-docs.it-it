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
- MSBuild (C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: bfa60ff0f7e4060f5725fe54bd5950d858b86a22
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272398"
---
# <a name="getoutofdateitems-task"></a>Attività GetOutOfDateItems

Attività di supporto che legge i tlog precedenti, scrive nuovi tlog e restituisce set di elementi che non sono aggiornati.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **GetOutOfDateItems**.

|Parametro|Descrizione|
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