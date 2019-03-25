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
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 183cdefbca29db486b84cb61f90501507e298838
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070410"
---
# <a name="custombuild-task"></a>Attività CustomBuild

Esegue il wrapping dello strumento del compilatore Visual C++, cmd.exe.

## <a name="parameters"></a>Parametri

La tabella seguente descrive i parametri dell'attività **CustomBuild**.

|Parametro|Description|
|---------------|-----------------|
|**BuildSuffix**|Parametro **string** facoltativo.|
|**Sources**|Parametro **ITaskItem[]** obbligatorio.|
|**TrackerLogDirectory**|Parametro **string** facoltativo.|

## <a name="see-also"></a>Vedere anche

[Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)