---
title: Attività FindAppConfigFile | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0033bcb21922d6f7e0204b1555fa2c46f8d91d50
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977565"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile (attività)
Trova il file *app.config*, se presente, negli elenchi disponibili.

## <a name="parameters"></a>Parametri
 Nella tabella che segue vengono descritti i parametri dell'attività `FindAppConfigFile` .

|Parametro|Description|
|---------------|-----------------|
|`AppConfigFile`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica il primo elemento corrispondente trovato nell'elenco, se presente.|
|`PrimaryList`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica l'elenco principale in cui eseguire la ricerca.|
|`SecondaryList`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica l'elenco secondario in cui eseguire la ricerca.|
|`TargetPath`|Parametro `String` obbligatorio.<br /><br /> Specifica il valore da aggiungere come metadati.|

## <a name="remarks"></a>Osservazioni
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedere anche
- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)