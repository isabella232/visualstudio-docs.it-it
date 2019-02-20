---
title: Attività ResolveNativeReference | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 31de2c146accd71ae1606be62ab06fa368e7fb89
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758548"
---
# <a name="resolvenativereference-task"></a>Attività ResolveNativeReference
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Risolve i riferimenti nativi. Implementa la classe <xref:Microsoft.Build.Tasks.ResolveNativeReference>. Questa classe supporta l'infrastruttura .NET Framework, che non può essere usata direttamente dal codice.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
 Nella tabella che segue vengono descritti i parametri dell'attività `ResolveNativeReference`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AdditionalSearchPaths`|Parametro [String](<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->)`[]` obbligatorio.<br /><br /> Ottiene o imposta i percorsi di ricerca per la risoluzione di identità di assembly di riferimenti nativi.|  
|`ContainedComComponents`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta i componenti COM dell'assembly nativo.|  
|`ContainedLooseEtcFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta i file Etc senza vincoli di compilazione elencati nel manifesto nativo.|  
|`ContainedLooseTlbFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta i file TLB separati dell'assembly nativo.|  
|`ContainedPrerequisiteAssemblies`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta gli assembly che devono essere presenti prima che il manifesto possa essere usato.|  
|`ContainedTypeLibraries`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta le librerie dei tipi dell'assembly nativo.|  
|`ContainingReferenceFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta i file di riferimento.|  
|`NativeReferences`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Ottiene o imposta i riferimenti all'assembly nativo Win32.|  
  
## <a name="remarks"></a>Osservazioni  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
