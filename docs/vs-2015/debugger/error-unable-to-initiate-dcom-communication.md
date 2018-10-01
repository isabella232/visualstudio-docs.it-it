---
title: 'Errore: Impossibile avviare la comunicazione DCOM | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c8ee1e5a9a9f799a4e9d5d8a4cc3b6f5e03b504
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526859"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Errore: impossibile avviare la comunicazione DCOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [errore: Impossibile avviare la comunicazione DCOM](https://docs.microsoft.com/visualstudio/debugger/error-unable-to-initiate-dcom-communication).  
  
Si è verificato un errore DCOM quando il computer locale ha tentato di comunicare con il computer remoto. Questo errore è causato dalla presenza di un firewall nel server remoto oppure dall'interruzione dell'autenticazione di Windows nel computer remoto.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Se nel computer remoto è abilitato Windows Firewall, vedere [Set Up the Remote Tools sul dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) per istruzioni su come configurare il firewall per il debug locale.  
  
-   Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer. Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug remoto](../debugger/remote-debugging.md)



