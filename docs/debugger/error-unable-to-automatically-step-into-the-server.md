---
title: "Errore: Impossibile eseguire automaticamente all'interno del Server | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, notification error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9d84f4c7f7f58ae980a266b436207c843926ae1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711735"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Errore: impossibile eseguire automaticamente l'istruzione sul server
Il testo del messaggio di errore è il seguente:

 Impossibile eseguire automaticamente l'istruzione sul server. Il debugger non ha ricevuto alcuna notifica prima dell'esecuzione della routine remota.

 Questo errore può verificarsi quando si tenta di eseguire un servizio Web. Per altre informazioni, vedere [Accesso a un servizio Web XML](https://msdn.microsoft.com/library/8e67de38-bf5f-41cc-a457-1b88ce63d764). L'errore è dovuto a una configurazione non corretta di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

 Possibili cause:

- Nel file web.config dell'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non viene impostato il debug su "true" (vedere [Modalità debug nelle applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- Una versione di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è stata installata dopo l'installazione di Visual Studio. Installare[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] prima di Visual Studio. Per risolvere il problema, usare **Pannello di controllo > Programmi e funzionalità** di Windows per ripristinare l'installazione di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)