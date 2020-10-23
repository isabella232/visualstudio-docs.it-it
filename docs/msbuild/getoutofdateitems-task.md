---
title: Attività GetOutOfDateItems | Microsoft Docs
description: Usare l'attività Helper MSBuild GetOutOfDateItems per leggere e scrivere i log delle transazioni (tlog) e restituire set di elementi che non sono aggiornati.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6cc80d4e1aa3580e0185460d19f78e9737b73220
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436819"
---
# <a name="getoutofdateitems-task"></a>Attività GetOutOfDateItems

Attività di supporto che legge i tlog precedenti, scrive nuovi tlog e restituisce set di elementi che non sono aggiornati.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **GetOutOfDateItems**.

|Parametro|Descrizione|
|---------------|-----------------|
|**CheckForInterdependencies**|Parametro **bool** facoltativo.|
|**CommandMetadataName**|Parametro **stringa** facoltativo.|
|**DependenciesMetadataName**|Parametro **stringa** facoltativo.|
|**HasInterdependencies**|Parametro di output **bool** facoltativo.|
|**OutOfDateSources**|Parametro di output facoltativo **ITaskItem[]**.|
|**OutputsMetadataName**|Parametro di **stringa** obbligatorio.|
|**recenti**|Parametro **ITaskItem []** facoltativo.|
|**TLogDirectory**|Parametro di **stringa** obbligatorio.|
|**TLogNamePrefix**|Parametro di **stringa** obbligatorio.|

## <a name="see-also"></a>Vedere anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)