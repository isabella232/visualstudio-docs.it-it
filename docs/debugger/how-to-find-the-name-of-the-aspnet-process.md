---
title: Trovare il processo ASP.NET in esecuzione | Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 54aa98dd238d7a78e4ae89af05dceae0f9911478
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187651"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Trovare il nome del processo ASP.NET

Per eseguire il debug di un'app [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in esecuzione, il debugger di Visual Studio deve connettersi al processo di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in base al nome.

**Per individuare il processo che esegue un'app ASP.NET:**

1. Con l'app in esecuzione, in Visual Studio selezionare **Debug** > **Connetti a processo**.

1. Nella finestra di dialogo **Connetti a processo** Digitare le prime lettere dei nomi di processo dall'elenco seguente oppure immetterle nella casella di ricerca. Quello che esegue è quello che esegue l'app ASP.NET. Connettersi a tale processo per eseguire il debug dell'app.

    - *w3wp. exe* è IIS 6,0 e versioni successive.
    - *Aspnet_wp. exe* è costituito da versioni precedenti di IIS.
    - *iisexpress.exe* is IISExpress.
    - *dotnet. exe* è ASP.NET Core.
    - *Inetinfo. exe* è un'applicazione ASP precedente eseguita in-process.

>[!NOTE]
>Visual Studio 2012 e versioni precedenti [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] codice possono trovarsi sul file system ed eseguire nel server di prova *WebDev. webserver. exe* o *WebDev. WebServer40. exe*. In questo caso, per il debug locale, connettersi a *WebDev. webserver. exe* o *WebDev. WebServer40. exe* anziché il processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

**Vedere anche:**

- [Connettersi a un processo in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Prerequisiti per il debug remoto di applicazioni Web](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md)
- [Eseguire il debug di applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)