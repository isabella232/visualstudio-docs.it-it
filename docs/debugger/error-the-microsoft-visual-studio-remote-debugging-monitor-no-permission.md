---
title: Microsoft Visual Studio Remote Debugging Monitor sul computer remoto non dispone dell'autorizzazione per connettersi al computer
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 150d49d25c8c39d927c64a2cd463a068559847b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871338"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Errore: Microsoft Visual Studio Remote Debugging Monitor sul computer remoto non dispone dell'autorizzazione per connettersi al computer.

Questo errore si verifica quando l'utente che tenta di eseguire Visual Studio Remote Debugging Monitor (msvsmon) non dispone di un account nel computer locale. Questo errore può verificarsi quando il debug remoto utilizza il motore di debug legacy.

## <a name="to-fix-this-problem"></a>Per risolvere il problema

- Aggiungere un account utente al computer host del debugger di Visual Studio, con lo stesso nome e password dell'account utente che esegue msvsmon nel computer remoto.

   \- - oppure -

- Eseguire msvsmon utilizzando un account utente che dispone dell'autorizzazione per l'invio di chiamate nel computer locale, ovvero di un account utente configurato come utente di dominio e amministratore nel computer in cui è in esecuzione msvsmon. L'account utente per l'esecuzione di msvsmon può essere specificato in due diversi modi:

  - Fare clic con il pulsante destro del mouse sull'icona di msvsmon e scegliere **Esegui come** dal menu di scelta rapida

    \- - oppure -

  - Al prompt dei comandi, digitare `runas.exe`.

## <a name="see-also"></a>Vedi anche

- [Errori e risoluzione dei problemi di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debug remoto](../debugger/remote-debugging.md)