---
title: 'Errore: Computer remoto non è stato possibile avviare le comunicazioni DCOM | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e936292010c73decffadc5b215156f2200ed8b3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683074"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Errore: il computer remoto non può avviare le comunicazioni DCOM
Quando il computer remoto ha tentato di comunicare con il computer locale si è verificato un errore DCOM. Il computer locale è il computer che

 esegue Visual Studio. L'errore può essere determinato da numerose cause:

-   Nel computer locale è stato attivato un firewall.

-   L'autenticazione di Windows dal computer remoto al computer locale non funziona.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1.  Se nel computer locale è abilitato Windows Firewall, vedere [debug remoto](../debugger/remote-debugging.md) per istruzioni su come configurare il firewall per il debug locale.

2.  Testare l'autenticazione di Windows tentando di aprire una condivisione di file nel computer locale dal server remoto.

3.  Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer. Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.

## <a name="see-also"></a>Vedere anche
 [Remote Debugging](../debugger/remote-debugging.md)