---
title: Trovare il processo ASP.NET in esecuzione | Microsoft Docs
description: Informazioni su come eseguire il debug di un'app ASP.NET in esecuzione. Il debugger di Visual Studio viene collegato al processo ASP.NET in base al nome.
ms.custom: SEO-VS-2020
ms.date: 11/04/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 11526639975924fd9984dce33a08e54c9a5405b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877655"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Trovare il nome del processo ASP.NET

Per eseguire il debug di un'app in esecuzione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , il debugger di Visual Studio deve connettersi al [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo in base al nome.

**Per individuare il processo che esegue un'app ASP.NET:**

1. Con l'app in esecuzione, in Visual Studio selezionare **debug**  >  **Connetti a processo**.

1. Nella finestra di dialogo **Connetti a processo** Digitare le prime lettere dei nomi di processo dall'elenco seguente oppure immetterle nella casella di ricerca. Quello che esegue è quello che esegue l'app ASP.NET. Connettersi a tale processo per eseguire il debug dell'app.

    - *w3wp.exe* è IIS 6,0 e versioni successive.
    - *aspnet_wp.exe* è costituito da versioni precedenti di IIS.
    - *iisexpress.exe* is IISExpress.
    - *dotnet.exe* è ASP.NET Core.
    - *inetinfo.exe* le applicazioni ASP precedenti sono in esecuzione in-process.

>[!NOTE]
>Visual Studio 2012 e il [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] codice precedente possono trovarsi sul file System ed essere eseguiti sul server di test *WebDev.WebServer.exe* o *WebDev.WebServer40.exe*. In questo caso, per il debug locale, connettersi a *WebDev.WebServer.exe* o *WebDev.WebServer40.exe* anziché al [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo.

**Vedere anche:**

- [Connettersi a un processo in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Prerequisiti per il debug remoto di applicazioni Web](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md)
- [Eseguire il debug di applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)