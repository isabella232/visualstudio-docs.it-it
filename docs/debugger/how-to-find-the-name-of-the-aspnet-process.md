---
title: Trovare il processo ASP.NET in esecuzione | Microsoft Docs
description: Informazioni su come eseguire il debug di un'app ASP.NET in esecuzione. Collegare il debugger Visual Studio al processo ASP.NET in base al nome.
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
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: ea5a2c954f031139c66616f80c4dc5b44d2efb5d8b0aa0329c5e043d4a75d909
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379126"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Trovare il nome del processo ASP.NET

Per eseguire il debug di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] un'app in esecuzione, Visual Studio debugger deve connettersi al [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo in base al nome.

**Per scoprire quale processo esegue un'app ASP.NET:**

1. Con l'app in esecuzione, in Visual Studio selezionare Debug Attach to Process **(Esegui debug**  >  **connessione a processo).**

1. Nella finestra **di dialogo Associa a** processo digitare le prime lettere dei nomi dei processi nell'elenco seguente o immetterle nella casella di ricerca. Quello in esecuzione è quello che esegue l'ASP.NET app. Connettersi a tale processo per eseguire il debug dell'app.

    - *w3wp.exe* è IIS 6.0 e versioni successive.
    - *aspnet_wp.exe* versioni precedenti di IIS.
    - *iisexpress.exe* is IISExpress.
    - *dotnet.exe* è ASP.NET Core.
    - *inetinfo.exe* sono applicazioni ASP meno recenti in esecuzione in-process.

>[!NOTE]
>Visual Studio 2012 e versioni precedenti possono essere nel file system ed essere eseguiti nel server di testWebDev.WebServer.exe[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o *WebDev.WebServer40.exe*.  In questo caso, per il debug locale, *connettersiWebDev.WebServer.exe* o *WebDev.WebServer40.exe* anziché al [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo.

**Vedere anche:**

- [Connettersi a un processo in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Prerequisiti per il debug remoto di applicazioni Web](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md)
- [Eseguire il debug di applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)