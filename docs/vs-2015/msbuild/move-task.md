---
title: Attività Move | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab75ccebd618946454c3386f564e3f6199409935
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191581"
---
# <a name="move-task"></a>Attività Move
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sposta i file in una nuova posizione.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Move`.  
  
|Parametro|DESCRIZIONE|  
|---------------|-----------------|  
|`DestinationFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica l'elenco di file in cui spostare i file di origine. Si presume che esista un mapping uno-a-uno tra questo elenco e quello specificato nel parametro `SourceFiles`. In altri termini, il primo file specificato in `SourceFiles` verrà spostato nel primo percorso specificato in `DestinationFiles` e così via.|  
|`DestinationFolder`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica la directory in cui spostare i file.|  
|`MovedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli elementi spostati correttamente.|  
|`OverwriteReadOnlyFiles`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, sovrascrive i file anche se sono contrassegnati come di sola lettura.|  
|`SourceFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file da spostare.|  
  
## <a name="remarks"></a>Osservazioni  
 È necessario specificare il parametro `DestinationFolder` o `DestinationFiles`, ma non entrambi. Se vengono specificati entrambi, l'attività avrà esito negativo e verrà registrato un errore.  
  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
