---
title: Attività FindAppConfigFile | Microsoft Docs
description: Informazioni su come usare l'attività FindAppConfigFile di MSBuild per trovare il file di app.config, se presente, negli elenchi forniti.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d186a72bcc7af18671c279ff392de066b6fd9fee
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2020
ms.locfileid: "92435676"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile (attività)

Trova il file di *app.config* , se presente, negli elenchi forniti.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `FindAppConfigFile` .

|Parametro|Descrizione|
|---------------|-----------------|
|`AppConfigFile`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica il primo elemento corrispondente trovato nell'elenco, se presente.|
|`PrimaryList`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica l'elenco principale in cui eseguire la ricerca.|
|`SecondaryList`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica l'elenco secondario in cui eseguire la ricerca.|
|`TargetPath`|Parametro `String` obbligatorio.<br /><br /> Specifica il valore da aggiungere come metadati.|

## <a name="remarks"></a>Commenti

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedere anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
