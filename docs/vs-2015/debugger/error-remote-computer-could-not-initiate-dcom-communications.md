---
title: 'Errore: il computer remoto non è riuscito ad avviare le comunicazioni DCOM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b8ddec2bdec09da1f1175b59c94db31841a1453f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697330"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Errore: il computer remoto non può avviare le comunicazioni DCOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando il computer remoto ha tentato di comunicare con il computer locale si è verificato un errore DCOM. Il computer locale è il computer che  
  
 esegue Visual Studio. L'errore può essere determinato da numerose cause:  
  
- Nel computer locale è stato attivato un firewall.  
  
- L'autenticazione di Windows dal computer remoto al computer locale non funziona.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1. Se il computer locale è Windows Firewall abilitato, vedere [configurare la strumenti remoti nel dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) per istruzioni su come configurare il firewall per il debug locale.  
  
2. Testare l'autenticazione di Windows tentando di aprire una condivisione di file nel computer locale dal server remoto.  
  
3. Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer. Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostare Remote Tools sul dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
