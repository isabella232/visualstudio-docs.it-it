---
title: 'Errore: La condivisione file di Windows è stata configurata... | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c45a1b74-61ec-4c64-9e2c-13051a4f50a5
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30a2fd01828d92fadeb901305f56ad8c65b863d3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803916"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Errore: la condivisione di file di Windows è stata configurata...
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La condivisione di file di Windows è stata configurata in modo da connettersi al computer remoto utilizzando un nome utente diverso. Ciò è incompatibile con il debug remoto.  
  
 La condivisione di file è attualmente configurata per la connessione al computer remoto con un nome utente diverso. Il debug remoto non è possibile in uno scenario di questo tipo.  
  
 Per correggere l'errore, accedere al computer utilizzando un altro nome account oppure modificare la configurazione della condivisione di file in base al nome account utilizzato per il debug.  
  
 Prima di connettersi al computer remoto utilizzando questo nome utente, è necessario disconnettersi dal computer.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Accedere al computer locale, ossia il computer da cui viene eseguito il debug, utilizzando l'altro nome account.  
  
     -oppure-  
  
     . Disconnettersi dal computer remoto, quindi riconfigurare la condivisione file per connettersi a un altro computer con il proprio nome account:  
  
    1.  Nel **avviare** dal menu **Accessori**e quindi fare clic su **prompt dei comandi**.  
  
    2.  Al prompt dei comandi di Windows digitare:  
  
         `net use /delete computer_name`  
  
    3.  Modificare le impostazioni di condivisione file utilizzando uno dei metodi illustrati nella Guida di windows.



