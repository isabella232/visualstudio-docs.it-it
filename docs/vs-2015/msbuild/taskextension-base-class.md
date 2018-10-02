---
title: Classe di base TaskExtension | Microsoft Docs
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
- MSBuild, tool task base class
- tool task base class [MSBuild]
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc755abe558491eb1b4c6e0e9575b4a9b8d47884
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520194"
---
# <a name="taskextension-base-class"></a>Classe di base TaskExtension
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [TaskExtension Base Class](https://docs.microsoft.com/visualstudio/msbuild/taskextension-base-class).  
  
  
Molte attività ereditano dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Questa catena di ereditarietà aggiunge diversi parametri alle attività che ne derivano. Questi parametri sono elencati in questo documento.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella seguente vengono descritti i parametri delle classi di base.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine> facoltativo.<br /><br /> Specifica l'interfaccia del motore di compilazione disponibile per le attività. Il motore di compilazione imposta automaticamente questo parametro per consentire alle attività di richiamarlo.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine2> facoltativo.<br /><br /> Specifica l'interfaccia del motore di compilazione disponibile per le attività. Il motore di compilazione imposta automaticamente questo parametro per consentire alle attività di richiamarlo.<br /><br /> Questa è una proprietà che consente agli autori di attività che ereditano da questa classe di non dovere eseguire il cast da `IBuildEngine` a `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine3> facoltativo.<br /><br /> Specifica l'interfaccia del motore di compilazione fornita dall'host.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parametro <xref:Microsoft.Build.Framework.ITaskHost> facoltativo.<br /><br /> Specifica l'istanza dell'oggetto host (può essere null). Il motore di compilazione imposta questa proprietà se l'IDE host ha associato un oggetto host a questa particolare attività.|  
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Parametro di sola lettura <xref:Microsoft.Build.Utilities.TaskLoggingHelper> facoltativo.<br /><br /> Ottiene un oggetto `TaskLoggingHelperExtension` che contiene metodi di registrazione delle attività.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)



