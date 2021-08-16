---
description: Quando il computer remoto ha tentato di comunicare con il computer locale si è verificato un errore DCOM.
title: Il computer remoto non è stato in grado di avviare le comunicazioni DCOM | Microsoft Docs
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3c316b87f35186b58b58ae0b8db93edeee3c4a56ab903847ec95187ffb4491a2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404478"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Errore: il computer remoto non può avviare le comunicazioni DCOM
Quando il computer remoto ha tentato di comunicare con il computer locale si è verificato un errore DCOM. Il computer locale è il computer che

 esegue Visual Studio. L'errore può essere determinato da numerose cause:

- Nel computer locale è stato attivato un firewall.

- L'autenticazione di Windows dal computer remoto al computer locale non funziona.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Se nel computer locale è abilitato Windows [](../debugger/remote-debugging.md) firewall, vedere Debug remoto per istruzioni su come configurare il firewall per il debug locale.

2. Testare l'autenticazione di Windows tentando di aprire una condivisione di file nel computer locale dal server remoto.

3. Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer. Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.

## <a name="see-also"></a>Vedi anche
 [Debug remoto](../debugger/remote-debugging.md)
