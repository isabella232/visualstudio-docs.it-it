---
title: Attività ResolveManifestFiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e3d5fd327e6ef9db5029697d502d27574a8a8f7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043219"
---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles (attività)
Risolve gli elementi seguenti del processo di compilazione nei file per la generazione del manifesto: elementi compilati, dipendenze, satelliti, contenuto, simboli di debug e documentazione.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `ResolveManifestFiles` .  
  
|Parametro|Description|  
|---------------|-----------------|  
|`DeploymentManifestEntryPoint`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il nome del manifesto della distribuzione.|  
|`EntryPoint`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica l'assembly gestito o un riferimento al manifesto ClickOnce che rappresenta il punto di ingresso al manifesto.|  
|`ExtraFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file aggiuntivi.|  
|`ManagedAssemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly gestiti.|  
|`NativeAssemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly nativi.|  
|`OutputAssemblies`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly generati.|  
|`OutputDeploymentManifestEntryPoint`|Parametro di ouput facoltativo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Specifica il punto di ingresso del manifesto della distribuzione dell'output.|  
|`OutputEntryPoint`|Parametro di ouput facoltativo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Specifica il punto di ingresso dell'output.|  
|`OutputFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file di output.|  
|`PublishFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file di pubblicazione.|  
|`SatelliteAssemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly satellite.|  
|`SigningManifests`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, i manifesti sono firmati.|  
|`TargetCulture`|Parametro `String` facoltativo.<br /><br /> Specifica le impostazioni cultura di destinazione per gli assembly satellite.|  
|`TargetFrameworkVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione di .NET Framework di destinazione.|  
  
## <a name="remarks"></a>Note  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)