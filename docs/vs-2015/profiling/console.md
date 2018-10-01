---
title: Console | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1117bf7113743bfd8db63353a5b032c869a97c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518217"
---
# <a name="console"></a>Console
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Console](https://docs.microsoft.com/visualstudio/profiling/console).  
  
L'opzione **Console** di VSPerfCmd.exe consente di avviare l'applicazione specificata in una nuova finestra del prompt dei comandi. **Console** può essere usata solo con l'opzione **Launch** di VSPerfCmd. Se l'applicazione non è un'applicazione della riga di comando, **Console** non ha alcun effetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>Parametri  
 nessuno  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 L'opzione **Console** può essere specificata solo in una riga di comando che contiene anche l'opzione **Launch**.  
  
 **Launch:** `AppName`  
 Avvia il profiler e l'applicazione specificata da `AppName`.  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)



