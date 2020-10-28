---
title: Attività CustomBuild | Microsoft Docs
description: Questo articolo descrive l'attività MSBuild CustomBuild, che viene usata da MSBuild per supportare la personalizzazione del processo di compilazione C++.
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
ms.openlocfilehash: 640c1e6ae286b45f8700709829140093452a9491
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796550"
---
# <a name="custombuild-task"></a>Attività CustomBuild

Esegue il wrapping dello strumento compilatore Microsoft C++ cmd.exe. Questa classe deriva da [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), ma non usa il rilevamento file per individuare le dipendenze di file. Affinché la compilazione incrementale funzioni correttamente, tutte le dipendenze devono essere specificate esplicitamente come AdditionalDependencies.

## <a name="parameters"></a>Parametri

La tabella seguente descrive i parametri dell'attività **CustomBuild** .

|Parametro|Descrizione|
|---------------|-----------------|
|**BuildSuffix**|Parametro **stringa** facoltativo.|
|**recenti**|Parametro **ITaskItem[]** obbligatorio.|
|**TrackerLogDirectory**|Parametro **stringa** facoltativo.|

## <a name="see-also"></a>Vedere anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
