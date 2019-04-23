---
title: 'Errore: Il server web non è configurato correttamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 643be465aab889b1f31e8fa75dba68261444bc31
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061008"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Errore: Il server Web non è configurato in modo corretto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Alcune cause possibili di questo errore sono:  
  
- Tentativo di eseguire il debug di un'applicazione Web .NET copiata in un computer diverso, rinominato manualmente o spostato.  
  
- Indisponibilità di un numero sufficiente di connessioni IIS. Per altre informazioni su come distribuire un sito Web in IIS, vedere [Creare un sito Web](http://www.iis.net/learn/get-started/getting-started-with-iis/create-a-web-site).  
  
- Se si prova a eseguire il debug di un'applicazione ASP.NET, vedere [Pubblicazione in IIS](https://docs.asp.net/en/latest/publishing/iis.html) per istruzioni su come eseguire la distribuzione in un computer remoto che esegue IIS 8 o versione successiva oppure [Remote Debugging ASP.NET on a Remote IIS 7.5 Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) per istruzioni su come eseguire la distribuzione in un computer remoto che esegue IIS 7.5.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: Errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
