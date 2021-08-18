---
title: Attività FindAppConfigFile | Microsoft Docs
description: Informazioni su come usare MSBuild'attività FindAppConfigFile per trovare il file app.config, se presente, negli elenchi forniti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 74aa121b76bd0ec1a63e7e60b52dc5e8a181225c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093853"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile (attività)

Trova il *app.config* file, se presente, negli elenchi forniti.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `FindAppConfigFile` .

|Parametro|Descrizione|
|---------------|-----------------|
|`AppConfigFile`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica il primo elemento corrispondente trovato nell'elenco, se presente.|
|`PrimaryList`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica l'elenco principale in cui eseguire la ricerca.|
|`SecondaryList`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica l'elenco secondario in cui eseguire la ricerca.|
|`TargetPath`|Parametro `String` obbligatorio.<br /><br /> Specifica il valore da aggiungere come metadati.|

## <a name="remarks"></a>Commenti

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
