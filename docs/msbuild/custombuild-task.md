---
title: Attività CustomBuild | Microsoft Docs
description: Questo articolo descrive l MSBuild'attività CustomBuild, usata da MSBuild per supportare la personalizzazione del processo di compilazione C++.
ms.custom: SEO-VS-2020
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
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 03c8c41aa50651354a490f31f4bfe71e2dae7cdef4d066fd8d45edb8e742e757
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397943"
---
# <a name="custombuild-task"></a>Attività CustomBuild

Esegue il wrapping dello strumento del compilatore Microsoft C++, cmd.exe. Questa classe deriva da [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), ma non usa il rilevamento file per individuare le dipendenze di file. Affinché la compilazione incrementale funzioni correttamente, tutte le dipendenze devono essere specificate esplicitamente come AdditionalDependencies.

## <a name="parameters"></a>Parametri

La tabella seguente descrive i parametri dell'attività **CustomBuild**.

|Parametro|Descrizione|
|---------------|-----------------|
|**BuildSuffix**|Parametro **di stringa** facoltativo.|
|**recenti**|Parametro **ITaskItem[]** obbligatorio.|
|**TrackerLogDirectory**|Parametro **di stringa** facoltativo.|

## <a name="see-also"></a>Vedi anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
