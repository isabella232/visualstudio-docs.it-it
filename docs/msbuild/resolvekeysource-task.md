---
title: "Attività ResolveKeySource | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: "10"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: cdbbdd476d37d19be63402b970beef84e9802fb5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="resolvekeysource-task"></a>Attività ResolveKeySource
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