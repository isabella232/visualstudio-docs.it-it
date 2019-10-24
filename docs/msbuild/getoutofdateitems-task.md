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
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: d3dc343c595606faf5bd31d7f087f7ba8d95f69e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747313"
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
|**OutOfDateSources**|Parametro di output facoltativo **ITaskItem[]** .|
|**OutputsMetadataName**|Parametro **string** obbligatorio.|
|**Sources**|Parametro **ITaskItem[]** facoltativo.|
|**TLogDirectory**|Parametro **string** obbligatorio.|
|**TLogNamePrefix**|Parametro **string** obbligatorio.|

## <a name="see-also"></a>Vedere anche

[Riferimento alle attività](../msbuild/msbuild-task-reference.md)