---
title: Assicurarsi che DNS sia configurato correttamente nel computer di destinazione | Microsoft Docs
description: Questo errore si verifica quando il computer di destinazione non è in grado di risolvere il nome del computer host del debugger Visual Studio.
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 871163bb5ee4e29eebd037b1c499addc06fc8d96
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161418"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Errore: verificare che il DNS sia configurato correttamente nel computer di destinazione.
Quando si tenta di eseguire il debug remoto, potrebbe essere visualizzato il seguente messaggio di errore:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.
```

 Questo errore si verifica quando il computer di destinazione non è in grado di risolvere il nome del computer host del debugger Visual Studio. Verificare le impostazioni DNS del computer di destinazione.

- Per informazioni sulla visualizzazione della configurazione del DNS in Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 oppure Windows Server 2008 R2, fare clic sul pulsante **Start**, scegliere **Guida e supporto tecnico** e quindi cercare le **impostazioni di modifica TCP/IP**.

- Per ulteriori informazioni, visitare il [sito Web Microsoft Windows](https://www.microsoft.com/windows/) e cercare le **impostazioni di modifica TCP/IP**.

  Se è possibile risolvere il problema DNS, è possibile provare a eseguire il debugger remoto con un account diverso. L'errore si verifica quando è in esecuzione il debugger remoto con l'account del sistema locale o l'account del servizio di rete. Se si esegue il debugger remoto con un altro account, è possibile usare l'autenticazione NTLM, che non richiede il DNS. . Per la procedura, vedere Errore: Il servizio Visual Studio Remote Debugger nel computer di destinazione non è in grado di [connettersi a questo computer.](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)
