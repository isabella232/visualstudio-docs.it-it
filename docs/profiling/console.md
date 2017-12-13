---
title: Console | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce6e9ca93d9cdca191db7db8f2eb3d144b74e40d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="console"></a>Console
L'opzione **Console** di VSPerfCmd.exe consente di avviare l'applicazione specificata in una nuova finestra del prompt dei comandi. **Console** può essere usata solo con l'opzione **Launch** di VSPerfCmd. Se l'applicazione non è un'applicazione della riga di comando, **Console** non ha alcun effetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>Parametri  
 Nessuno  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 L'opzione **Console** può essere specificata solo in una riga di comando che contiene anche l'opzione **Launch**.  
  
 **Launch:** `AppName`  
 Avvia il profiler e l'applicazione specificata da `AppName`.  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)