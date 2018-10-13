---
title: Attività ResolveNonMSBuildProjectOutput | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a7d5ff4d38d1f494e706f833a387061323744660
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197190"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>Attività ResolveNonMSBuildProjectOutput
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Determina i file di output per riferimenti a progetti non MSBuild.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `ResolveNonMSBuildProjectOutput` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa XML che contiene gli output di progetto risolti.|  
|`ProjectReferences`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i riferimenti al progetto.|  
|`ResolvedOutputPaths`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco dei percorsi di riferimento risolti e conserva gli attributi dei riferimenti al progetto originali.|  
|`UnresolvedProjectReferences`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco degli elementi di riferimento del progetto che non sono stati risolti usando l'elenco di output prerisolto.<br /><br /> Poiché Visual Studio prerisolve solo progetti non MSBuild, questo significa che i riferimenti di progetto in questo elenco sono nel formato MSBuild.|  
  
## <a name="remarks"></a>Note  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)



