---
title: 'Errore: Non è possibile avviare la comunicazione DCOM | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_server_failed
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
ms.openlocfilehash: 1112ec72e8aca764f749a6d8f1925302f569b17e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044784"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Errore: Impossibile iniziare la comunicazione DCOM
Si è verificato un errore DCOM quando il computer locale ha tentato di comunicare con il computer remoto. Questo errore è causato dalla presenza di un firewall nel server remoto oppure dall'interruzione dell'autenticazione di Windows nel computer remoto.

### <a name="to-correct-this-error"></a>Per correggere l'errore

- Se nel computer remoto è abilitato Windows Firewall, vedere [debug remoto](../debugger/remote-debugging.md) per istruzioni su come configurare il firewall per il debug locale.

- Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer. Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.

## <a name="see-also"></a>Vedere anche
- [Remote Debugging](../debugger/remote-debugging.md)