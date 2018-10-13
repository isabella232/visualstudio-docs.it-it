---
title: 'Errore: Timeout durante il debug dei servizi Web | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b84ac5a8142250f9c71d9617a6717a1962b7106
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190333"
---
# <a name="error-timeout-while-debugging-web-services"></a>Errore: timeout durante il debug dei servizi Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Durante l'accesso a un servizio Web XML dal codice chiamante, è possibile che si verifichi un timeout con conseguente interruzione del debug. Potrebbe essere visualizzato un messaggio di errore simile al seguente.  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>Soluzione  
 Per evitare che si verifichi questo problema, impostare il valore di timeout per la chiamata al servizio Web XML su un valore infinito, come illustrato nell'esempio riportato di seguito:  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



