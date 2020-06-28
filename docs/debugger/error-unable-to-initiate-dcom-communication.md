---
title: Errore-Impossibile avviare la comunicazione DCOM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: ccd8b30fcba11d89e11227861c4582ff67f3a7e7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460026"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Errore: impossibile avviare la comunicazione DCOM
Si è verificato un errore DCOM quando il computer locale ha tentato di comunicare con il computer remoto. Questo errore è causato dalla presenza di un firewall nel server remoto oppure dall'interruzione dell'autenticazione di Windows nel computer remoto.

### <a name="to-correct-this-error"></a>Per correggere l'errore

- Se il computer remoto è abilitato Windows Firewall, vedere [Remote Debugging](../debugger/remote-debugging.md) per istruzioni su come configurare il firewall per il debug locale.

- Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer. Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.

## <a name="see-also"></a>Vedi anche
- [Debug remoto](../debugger/remote-debugging.md)