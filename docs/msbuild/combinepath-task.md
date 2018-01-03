---
title: "Attività CombinePath | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f67014faf67d0855ba7e800ad66e014eb665efc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="combinepath-task"></a>Attività CombinePath
Combina i percorsi specificati in un singolo percorso.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
 La tabella seguente descrive i parametri dell'[attività CombinePath](../msbuild/combinepath-task.md).  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`BasePath`|Parametro `String` obbligatorio.<br /><br /> Percorso base da combinare con gli altri percorsi. Può essere un percorso relativo, assoluto o vuoto.|  
|`Paths`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Elenco di singoli percorsi da combinare con l'oggetto BasePath per formare il percorso combinato. I percorsi possono essere relativi o assoluti.|  
|`CombinedPaths`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Percorso combinato creato da questa attività.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)