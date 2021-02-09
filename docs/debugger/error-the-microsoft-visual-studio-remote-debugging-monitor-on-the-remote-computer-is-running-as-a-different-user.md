---
title: Microsoft Visual Studio Remote Debugging Monitor è in esecuzione sul computer remoto come utente diverso
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 03e4ef05c1615e7798cd111f9cc5f95976abeebc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871325"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Errore: Microsoft Visual Studio Remote Debugging Monitor è in esecuzione sul computer remoto come utente diverso
Quando si tenta di eseguire il debug remoto, potrebbe essere visualizzato il seguente messaggio di errore:

 Microsoft Visual Studio Remote Debugging Monitor è in esecuzione sul computer remoto come utente diverso.

## <a name="cause"></a>Causa
 Questo messaggio viene visualizzato quando si esegue il debug in modalità Nessuna autenticazione e l'utente che ha avviato msvsmon non è lo stesso che esegue Visual Studio.

## <a name="solution"></a>Soluzione
 La soluzione ottimale, anche dal punto di vista della sicurezza, consiste nell'eseguire Remote Debugging Monitor (msvsmon.exe) utilizzando lo stesso account utente di Visual Studio. Se non è possibile, eseguire Remote Debugging Monitor utilizzando l'altro account con l'opzione **Consenti di eseguire il debug a qualunque utente** nella finestra di dialogo **Opzioni** di Remote Debugging Monitor.

> [!CAUTION]
> Se si concede ad altri utenti l'autorizzazione per la connessione, è possibile che si verifichino problemi di connessione alla sessione di debug remoto errata. Il debug in modalità **Nessuna autenticazione** non offre alcun livello di sicurezza e deve essere usato con cautela.

## <a name="see-also"></a>Vedi anche
- [Errori e risoluzione dei problemi di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debug remoto](../debugger/remote-debugging.md)