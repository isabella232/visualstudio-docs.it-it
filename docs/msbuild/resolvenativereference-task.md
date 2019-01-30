---
title: Attività ResolveNativeReference | Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b88e03f03eb0568ba2b71324010b19990f917b4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035991"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference (attività)
Risolve i riferimenti nativi. Implementa la classe <xref:Microsoft.Build.Tasks.ResolveNativeReference>. Questa classe supporta l'infrastruttura .NET Framework, che non può essere usata direttamente dal codice.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
 Nella tabella che segue vengono descritti i parametri dell'attività `ResolveNativeReference` .  
  
|Parametro|Description|  
|---------------|-----------------|  
|`AdditionalSearchPaths`|Parametro <xref:System.String?displayProperty=fullName>`[]` obbligatorio.<br /><br /> Ottiene o imposta i percorsi di ricerca per la risoluzione di identità di assembly di riferimenti nativi.|  
|`ContainedComComponents`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta i componenti COM dell'assembly nativo.|  
|`ContainedLooseEtcFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta i file *Etc* senza vincoli di compilazione elencati nel manifesto nativo.|  
|`ContainedLooseTlbFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta i file con estensione *tlb* separati dell'assembly nativo.|  
|`ContainedPrerequisiteAssemblies`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta gli assembly che devono essere presenti prima che il manifesto possa essere usato.|  
|`ContainedTypeLibraries`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta le librerie dei tipi dell'assembly nativo.|  
|`ContainingReferenceFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta i file di riferimento.|  
|`NativeReferences`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Ottiene o imposta i riferimenti all'assembly nativo Win32.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)