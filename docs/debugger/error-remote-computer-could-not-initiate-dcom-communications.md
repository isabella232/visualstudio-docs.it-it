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
ms.openlocfilehash: 7ceb796b3a4b3cbc2b239a09ac8c173e746f194c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091200"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Errore: Il computer remoto non può iniziare le comunicazioni DCOM
Quando il computer remoto ha tentato di comunicare con il computer locale si è verificato un errore DCOM. Il computer locale è il computer che

 esegue Visual Studio. L'errore può essere determinato da numerose cause:

- Nel computer locale è stato attivato un firewall.

- L'autenticazione di Windows dal computer remoto al computer locale non funziona.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Se nel computer locale è abilitato Windows Firewall, vedere [debug remoto](../debugger/remote-debugging.md) per istruzioni su come configurare il firewall per il debug locale.

2. Testare l'autenticazione di Windows tentando di aprire una condivisione di file nel computer locale dal server remoto.

3. Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer. Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.

## <a name="see-also"></a>Vedere anche
 [Remote Debugging](../debugger/remote-debugging.md)