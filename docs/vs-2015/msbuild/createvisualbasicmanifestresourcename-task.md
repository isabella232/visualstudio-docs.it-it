---
title: Attività CreateVisualBasicManifestResourceName | Microsoft Docs
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
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d923c83c513ff33b971e1b5ca77109d6ff057db7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184071"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>Attività CreateVisualBasicManifestResourceName
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Crea un nome di manifesto di tipo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] dal nome di un determinato file con estensione resx o da un'altra risorsa.  
  
## <a name="parameters"></a>Parametri  
 La tabella seguente descrive i parametri dell'[attività CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md).  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`ManifestResourceNames`|<xref:Microsoft.Build.Framework.ITaskItem>`[]`parametro di sola lettura di output.<br /><br /> Nomi di manifesto risultanti.|  
|`ResourceFiles`|Parametro `String` obbligatorio.<br /><br /> Nome del file di risorse da cui creare il nome del manifesto [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].|  
|`RootNamespace`|Parametro `String` facoltativo.<br /><br /> Spazio dei nomi radice del file di risorse, in genere derivato dal file di progetto. Può essere `null`.|  
|`PrependCultureAsDirectory`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, il nome delle impostazioni cultura viene aggiunto come nome di directory prima del nome di risorsa di manifesto. Il valore predefinito è `true`.|  
|`ResourceFilesWithManifestResourceNames`|Parametro di output di sola lettura `String` facoltativo.<br /><br /> Restituisce il nome del file di risorse che include ora il nome di risorsa di manifesto.|  
  
## <a name="remarks"></a>Osservazioni  
 L'[attività CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) determina il nome di risorsa di manifesto appropriato da assegnare a un file con estensione resx specificato o a un altro file di risorse. L'attività fornisce un nome logico a un file di risorse e quindi lo associa a un parametro di output come metadato.  
  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento attività](../msbuild/msbuild-task-reference.md)
