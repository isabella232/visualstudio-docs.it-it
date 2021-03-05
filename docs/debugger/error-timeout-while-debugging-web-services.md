---
description: Durante l'accesso a un servizio Web XML dal codice chiamante, è possibile che si verifichi un timeout con conseguente interruzione del debug.
title: Timeout durante il debug dei servizi Web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 338dd92b69760c395554a878b36fc4bab05e09a3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146509"
---
# <a name="error-timeout-while-debugging-web-services"></a>Errore: timeout durante il debug dei servizi Web
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

## <a name="see-also"></a>Vedi anche
- [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
