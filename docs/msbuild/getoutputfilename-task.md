---
title: Attività GetOutputFileName | Microsoft Docs
description: Utilizzare l'attività Helper MSBuild GetOutputFileName per specificare le opzioni relative al nome del file di output per cl.exe e altri strumenti.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: cb4670bb84b151332951608f7b20ef5ea44e59a3
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436782"
---
# <a name="getoutputfilename-task"></a>Attività GetOutputFileName

Attività di supporto per ottenere il nome del file di output per cl e altri strumenti, che consentono di specificare solo la directory di output o il nome di file completo o nulla.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **GetOutputFileName**.

|Parametro|Descrizione|
|---------------|-----------------|
|**OutputExtension**|Parametro di **stringa** obbligatorio.|
|**OutputFile**|Parametro di output **string** facoltativo.|
|**Percorso output**|Parametro **stringa** facoltativo.|
|**SourceFile**|Parametro di **stringa** obbligatorio.|

## <a name="see-also"></a>Vedere anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
