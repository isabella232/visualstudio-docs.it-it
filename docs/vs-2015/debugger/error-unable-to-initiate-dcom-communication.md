---
title: 'Errore: Non è possibile avviare la comunicazione DCOM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f9ae4de4f8dc044d578bb4f593dc9c6c77a7b0b6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60083894"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Errore: Impossibile iniziare la comunicazione DCOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si è verificato un errore DCOM quando il computer locale ha tentato di comunicare con il computer remoto. Questo errore è causato dalla presenza di un firewall nel server remoto oppure dall'interruzione dell'autenticazione di Windows nel computer remoto.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Se nel computer remoto è abilitato Windows Firewall, vedere [Set Up the Remote Tools sul dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) per istruzioni su come configurare il firewall per il debug locale.  
  
- Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer. Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.  
  
## <a name="see-also"></a>Vedere anche  
 [Remote Debugging](../debugger/remote-debugging.md)
