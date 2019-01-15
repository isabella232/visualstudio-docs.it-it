---
title: 'Errore: Timeout durante il debug dei servizi Web | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98d112528ace581c9173e82af63c502e2124315a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53832571"
---
# <a name="error-timeout-while-debugging-web-services"></a>Errore: Timeout durante il debug dei servizi Web
Durante l'accesso a un servizio Web XML dal codice chiamante, è possibile che si verifichi un timeout con conseguente interruzione del debug. Potrebbe essere visualizzato un messaggio di errore simile al seguente.  
  
```cmd
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>Soluzione  
 Per evitare che si verifichi questo problema, impostare il valore di timeout per la chiamata al servizio Web XML su un valore infinito, come illustrato nell'esempio riportato di seguito:  
  
```csharp
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: Errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
