---
title: 'Errore: Condivisione file di Windows è stata configurata... | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
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
ms.openlocfilehash: 257d7a0ce597cc8cbbadca975ee3db60d4e3adcc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951846"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Errore: La condivisione di file di Windows è stata configurata...
La condivisione di file di Windows è stata configurata in modo da connettersi al computer remoto utilizzando un nome utente diverso. Ciò è incompatibile con il debug remoto.  
  
 La condivisione di file è attualmente configurata per la connessione al computer remoto con un nome utente diverso. Il debug remoto non è possibile in uno scenario di questo tipo.  
  
 Per correggere l'errore, accedere al computer utilizzando un altro nome account oppure modificare la configurazione della condivisione di file in base al nome account utilizzato per il debug.  
  
 Prima di connettersi al computer remoto utilizzando questo nome utente, è necessario disconnettersi dal computer.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Accedere al computer locale, ossia il computer da cui viene eseguito il debug, utilizzando l'altro nome account.  
  
     -oppure-  
  
     . Disconnettersi dal computer remoto, quindi riconfigurare la condivisione file per connettersi a un altro computer con il proprio nome account:  
  
    1.  Fare clic sul pulsante **Start**, scegliere **Accessori**, quindi **Prompt dei comandi**.  
  
    2.  Al prompt dei comandi di Windows digitare:  
  
         `net use /delete computer_name`  
  
    3.  Modificare le impostazioni di condivisione file utilizzando uno dei metodi illustrati nella Guida di windows.