---
title: "Errore: Microsoft Visual Studio Remote Debugging Monitor sul computer remoto non dispone dell'autorizzazione per connettersi al computer"
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac6e632927878988f8a3ff86d63fea080a45bd6d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850443"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Errore: Microsoft Visual Studio Remote Debugging Monitor sul computer remoto non dispone dell'autorizzazione per connettersi al computer

Questo errore si verifica quando l'utente che tenta di eseguire Visual Studio Remote Debugging Monitor (msvsmon) non dispone di un account nel computer locale.

## <a name="to-fix-this-problem"></a>Per risolvere il problema

- Aggiungere un account utente al computer host del debugger di Visual Studio, con lo stesso nome e password dell'account utente che esegue msvsmon nel computer remoto.

   \- oppure -

- Eseguire msvsmon utilizzando un account utente che dispone dell'autorizzazione per l'invio di chiamate nel computer locale, ovvero di un account utente configurato come utente di dominio e amministratore nel computer in cui è in esecuzione msvsmon. L'account utente per l'esecuzione di msvsmon può essere specificato in due diversi modi:

  - Fare clic con il pulsante destro del mouse sull'icona di msvsmon e scegliere **Esegui come** dal menu di scelta rapida

    \- oppure -

  - Al prompt dei comandi, digitare `runas.exe`.

## <a name="see-also"></a>Vedere anche

- [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)