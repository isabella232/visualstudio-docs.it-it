---
title: Il computer remoto non è riuscito ad avviare le comunicazioni DCOM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 92a03c89cfd1bf0e0772d1a1728ffb9b0754d089
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852589"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Errore: il computer remoto non può avviare le comunicazioni DCOM
Quando il computer remoto ha tentato di comunicare con il computer locale si è verificato un errore DCOM. Il computer locale è il computer che

 esegue Visual Studio. L'errore può essere determinato da numerose cause:

- Nel computer locale è stato attivato un firewall.

- L'autenticazione di Windows dal computer remoto al computer locale non funziona.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Se il computer locale è abilitato Windows Firewall, vedere [Remote Debugging](../debugger/remote-debugging.md) per istruzioni su come configurare il firewall per il debug locale.

2. Testare l'autenticazione di Windows tentando di aprire una condivisione di file nel computer locale dal server remoto.

3. Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer. Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.

## <a name="see-also"></a>Vedere anche
 [Debug remoto](../debugger/remote-debugging.md)