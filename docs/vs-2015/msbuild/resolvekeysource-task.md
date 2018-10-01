---
title: Attività ResolveKeySource | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a51b9b07be214a6713da4d9d6f9ccf99814b270f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531454"
---
# <a name="resolvekeysource-task"></a>Attività ResolveKeySource
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [attività ResolveKeySource](https://docs.microsoft.com/visualstudio/msbuild/resolvekeysource-task).  
  
  
Determina l'origine delle chiavi con nome sicuro.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
 Nella tabella che segue vengono descritti i parametri dell'attività `ResolveKeySource`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|Parametro `Int32` facoltativo.<br /><br /> Ottiene o imposta la quantità di tempo in secondi durante i quali visualizzare il messaggio del conto alla rovescia.|  
|`AutoClosePasswordPromptTimeout`|Parametro `Int32` facoltativo.<br /><br /> Ottiene o imposta la quantità di tempo di attesa, in secondi, prima di chiudere la finestra di dialogo di richiesta della password.|  
|`CertificateFile`|Parametro `String` facoltativo.<br /><br /> Ottiene o imposta il percorso del file di certificato.|  
|`CertificateThumbprint`|Parametro `String` facoltativo.<br /><br /> Ottiene o imposta l'identificazione personale del certificato.|  
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Ottiene o imposta il percorso del file della chiave.|  
|`ResolvedKeyContainer`|Parametro di ouput facoltativo `String`.<br /><br /> Ottiene o imposta il contenitore di chiavi risolte.|  
|`ResolvedKeyFile`|Parametro di ouput facoltativo `String`.<br /><br /> Ottiene o imposta il file di chiave risolto.|  
|`ResolvedThumbprint`|Parametro di ouput facoltativo `String`.<br /><br /> Ottiene o imposta l'identificazione personale del certificato risolta.|  
|`ShowImportDialogDespitePreviousFailures`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, visualizza la finestra di dialogo di importazione indipendentemente dagli errori precedenti.|  
|`SuppressAutoClosePasswordPrompt`|Parametro `Boolean` facoltativo.<br /><br /> Ottiene o imposta un valore booleano che specifica se la finestra di dialogo di richiesta della password non dovrebbe chiudersi automaticamente.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)



