---
title: Attività Move | Microsoft Docs
description: Informazioni sui parametri e le impostazioni per l'MSBuild Sposta, che sposta i file in nuove posizioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 761d499c01fdc2fda0a7f8e539377a9ce2bb50edb8e33429cf799265ac59c494
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270510"
---
# <a name="move-task"></a>Move (attività)

Sposta i file in una nuova posizione.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `Move`.

|Parametro|Descrizione|
|---------------|-----------------|
|`DestinationFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica l'elenco di file in cui spostare i file di origine. Si presume che esista un mapping uno-a-uno tra questo elenco e quello specificato nel parametro `SourceFiles`. In altri termini, il primo file specificato in `SourceFiles` verrà spostato nel primo percorso specificato in `DestinationFiles` e così via.|
|`DestinationFolder`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica la directory in cui spostare i file.|
|`MovedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli elementi spostati correttamente.|
|`OverwriteReadOnlyFiles`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, sovrascrive i file anche se sono contrassegnati come di sola lettura.|
|`SourceFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file da spostare.|

## <a name="remarks"></a>Commenti

 È necessario specificare il parametro `DestinationFolder` o `DestinationFiles`, ma non entrambi. Se vengono specificati entrambi, l'attività avrà esito negativo e verrà registrato un errore.

 L'attività `Move` crea le cartelle necessarie per i file di destinazione desiderati.

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
