---
title: Attività GetOutputFileName | Microsoft Docs
description: Usare l MSBuild'attività helper GetOutputFileName per specificare le opzioni del nome file di output per cl.exe e altri strumenti.
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
ms.openlocfilehash: 5de0fab9f6aa3b6a57248b4f236e816fe60bdd44c76a55cd466ea287fd9c38d6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397631"
---
# <a name="getoutputfilename-task"></a>Attività GetOutputFileName

Attività di supporto per ottenere il nome del file di output per cl e altri strumenti, che consentono di specificare solo la directory di output o il nome di file completo o nulla.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **GetOutputFileName**.

|Parametro|Descrizione|
|---------------|-----------------|
|**OutputExtension**|Parametro **di stringa** obbligatorio.|
|**Outputfile**|Parametro di output **string** facoltativo.|
|**Percorso output**|Parametro **di stringa** facoltativo.|
|**SourceFile**|Parametro **di stringa** obbligatorio.|

## <a name="see-also"></a>Vedi anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
