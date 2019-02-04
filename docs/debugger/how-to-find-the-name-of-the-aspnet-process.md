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
ms.openlocfilehash: 120b5b6818900b8f177a7358d9ef0cee7bb88482
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992620"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Trovare il nome del processo ASP.NET

Eseguire il debug di un in esecuzione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] app, il debugger di Visual Studio deve connettersi il [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processi in base al nome.

**Per scoprire quale processo è in esecuzione un'app ASP.NET:**

1. Con l'app in esecuzione, in Visual Studio, selezionare **Debug** > **Connetti a processo**. 
   
1. Nel **Connetti a processo** finestra di dialogo, digitare le prime lettere del processo di nomi nell'elenco seguente o immetterli nella casella di ricerca. Quello che esegue è quella in esecuzione l'app ASP.NET. Connettersi a tale processo per eseguire il debug dell'app. 
   
    - *w3wp.exe* è IIS 6.0 e versioni successive. 
    - *aspnet_wp.exe* sia le versioni precedenti di IIS.
    - *iisexpress.exe* is IISExpress.
    - *dotnet.exe* è ASP.NET Core.
    - *Inetinfo.exe* è meno recente applicazioni ASP in esecuzione in-process. 

>[!NOTE]
>Visual Studio 2012 e versioni precedente [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] codice può essere nel file system ed eseguito sul server di prova *WebDev.WebServer.exe* oppure *WebDev.WebServer40.exe*. In questo caso, per il debug locale, collegato a *WebDev.WebServer.exe* oppure *WebDev.WebServer40.exe* anziché il [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo. 

**Vedere anche:**

 [Connettersi a un processo in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [Prerequisiti per il debug remoto di applicazioni web](/visualstudio/debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer)   
 [Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md)   
 [Eseguire il debug di applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)