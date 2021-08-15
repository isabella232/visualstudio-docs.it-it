---
title: Attività GetOutOfDateItems | Microsoft Docs
description: Usare l MSBuild'attività helper GetOutOfDateItems per leggere e scrivere log delle transazioni (TLOG) e restituire set di elementi non aggiornati.
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
ms.openlocfilehash: 26810b5e2102cc6430184eca99ba8b15f0dca516661f30c76534efb8ab152e0f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270744"
---
# <a name="getoutofdateitems-task"></a>Attività GetOutOfDateItems

Attività di supporto che legge i tlog precedenti, scrive nuovi tlog e restituisce set di elementi che non sono aggiornati.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **GetOutOfDateItems**.

|Parametro|Descrizione|
|---------------|-----------------|
|**CheckForInterdependencies**|Parametro **bool** facoltativo.|
|**CommandMetadataName**|Parametro **di stringa** facoltativo.|
|**DependenciesMetadataName**|Parametro **di stringa** facoltativo.|
|**HasInterdependencies**|Parametro di output **bool** facoltativo.|
|**OutOfDateSources**|Parametro di output facoltativo **ITaskItem[]**.|
|**OutputsMetadataName**|Parametro **di stringa** obbligatorio.|
|**recenti**|Parametro **ITaskItem[]** facoltativo.|
|**TLogDirectory**|Parametro **di stringa** obbligatorio.|
|**TLogNamePrefix**|Parametro **di stringa** obbligatorio.|

## <a name="see-also"></a>Vedi anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)