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
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d66a7be3751e74ff75787ef194f90da1dcd1d3ce
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593291"
---
# <a name="getoutputfilename-task"></a>Attività GetOutputFileName

Attività di supporto per ottenere il nome del file di output per cl e altri strumenti, che consentono di specificare solo la directory di output o il nome di file completo o nulla.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **GetOutputFileName**.

|Parametro|Descrizione|
|---------------|-----------------|
|**OutputExtension**|Parametro **di stringa** obbligatorio.|
|**Outputfile**|Parametro di output **string** facoltativo.|
|**Percorso output**|Parametro **stringa** facoltativo.|
|**SourceFile**|Parametro **di stringa** obbligatorio.|

## <a name="see-also"></a>Vedere anche

[Riferimento alle attività](../msbuild/msbuild-task-reference.md)
