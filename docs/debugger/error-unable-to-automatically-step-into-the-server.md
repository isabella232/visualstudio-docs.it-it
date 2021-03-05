---
title: Non è possibile eseguire automaticamente l'istruzione nel server | Microsoft Docs
description: Impossibile eseguire automaticamente l'istruzione sul server. Il debugger non ha ricevuto alcuna notifica prima dell'esecuzione della procedura remota.
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a374afef2dea92fbad72c45e35ca06904d75cbbe
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146483"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Errore: impossibile eseguire automaticamente l'istruzione sul server
Il testo dell'errore è simile al seguente:

 Impossibile eseguire automaticamente l'istruzione sul server. Il debugger non ha ricevuto alcuna notifica prima dell'esecuzione della routine remota.

 Questo errore può verificarsi quando si tenta di eseguire un servizio Web. Per altre informazioni, vedere [Accesso a un servizio Web XML](/previous-versions/zc57803s(v=vs.100)). L'errore è dovuto a una configurazione non corretta di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

 Le cause possibili sono:

- Nel file web.config dell'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non viene impostato il debug su "true" (vedere [Modalità debug nelle applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- Una versione di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è stata installata dopo l'installazione di Visual Studio. Installare[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] prima di Visual Studio. Per risolvere il problema, usare **Pannello di controllo > Programmi e funzionalità** di Windows per ripristinare l'installazione di Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Errori e risoluzione dei problemi di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debug remoto](../debugger/remote-debugging.md)
