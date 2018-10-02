---
title: Attività CreateCSharpManifestResourceName | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf5f98d4eddf7daa6099b97d805a50c59902572c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525729"
---
# <a name="createcsharpmanifestresourcename-task"></a>Attività CreateCSharpManifestResourceName
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [attività CreateCSharpManifestResourceName](https://docs.microsoft.com/visualstudio/msbuild/createcsharpmanifestresourcename-task).  
  
  
Crea un nome di manifesto di tipo [!INCLUDE[csprcs](../includes/csprcs-md.md)] dal nome di un determinato file con estensione resx o da un'altra risorsa.  
  
## <a name="parameters"></a>Parametri  
 La tabella seguente descrive i parametri dell'[attività CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md).  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`ManifestResourceNames`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> `[]` di output di sola lettura.<br /><br /> Nomi di manifesto risultanti.|  
|`ResourceFiles`|Parametro `String` obbligatorio.<br /><br /> Nome del file di risorse da cui creare il nome del manifesto [!INCLUDE[csprcs](../includes/csprcs-md.md)].|  
|`RootNamespace`|Parametro `String` facoltativo.<br /><br /> Spazio dei nomi radice del file di risorse, in genere derivato dal file di progetto. Può essere `null`.|  
|`PrependCultureAsDirectory`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, il nome delle impostazioni cultura viene aggiunto come nome di directory prima del nome di risorsa di manifesto. Il valore predefinito è `true`.|  
|`ResourceFilesWithManifestResourceNames`|Parametro di output di sola lettura `String` facoltativo.<br /><br /> Restituisce il nome del file di risorse che include ora il nome di risorsa di manifesto.|  
  
## <a name="remarks"></a>Note  
 L'[attività CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) determina il nome di risorsa di manifesto appropriato da assegnare a un file con estensione resx specificato o a un altro file di risorse. L'attività fornisce un nome logico a un file di risorse e quindi lo associa a un parametro di output come metadato.  
  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)



