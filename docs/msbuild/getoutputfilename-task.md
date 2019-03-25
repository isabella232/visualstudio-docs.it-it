---
title: Attività GetOutputFileName | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutputfilename
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: ee44e891c8c5f6a95971cade0536b2a5ec5b4688
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070428"
---
# <a name="getoutputfilename-task"></a>Attività GetOutputFileName

Attività di supporto per ottenere il nome del file di output per cl e altri strumenti, che consentono di specificare solo la directory di output o il nome di file completo o nulla.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **GetOutputFileName**.

|Parametro|Description|
|---------------|-----------------|
|**OutputExtension**|Parametro **string** obbligatorio.|
|**OutputFile**|Parametro di output **string** facoltativo.|
|**OutputPath**|Parametro **string** facoltativo.|
|**SourceFile**|Parametro **string** obbligatorio.|

## <a name="see-also"></a>Vedere anche

[Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)