---
title: Attività CombinePath | Microsoft Docs
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
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b97714fc707d8f9174a01dcc1fe7b3b59176de2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160389"
---
# <a name="combinepath-task"></a>Attività CombinePath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Combina i percorsi specificati in un singolo percorso.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
 Nella tabella seguente vengono descritti i parametri dell' [attività CombinePath](../msbuild/combinepath-task.md).  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`BasePath`|Parametro `String` obbligatorio.<br /><br /> Percorso base da combinare con gli altri percorsi. Può essere un percorso relativo, assoluto o vuoto.|  
|`Paths`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Elenco di singoli percorsi da combinare con l'oggetto BasePath per formare il percorso combinato. I percorsi possono essere relativi o assoluti.|  
|`CombinedPaths`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Percorso combinato creato da questa attività.|  
  
## <a name="remarks"></a>Osservazioni  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento attività](../msbuild/msbuild-task-reference.md)
