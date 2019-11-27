---
title: 'Errore: verificare che il DNS sia configurato correttamente nel computer di destinazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6815e21d0fe7af3a24f2fc36a4f448ec420c89de
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299750"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Errore: verificare che il DNS sia configurato correttamente nel computer di destinazione.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si tenta di eseguire il debug remoto, potrebbe essere visualizzato il seguente messaggio di errore:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Questo errore si verifica quando il computer di destinazione non è in grado di risolvere il nome del computer host del debugger Visual Studio. Verificare le impostazioni DNS del computer di destinazione.  
  
- Per informazioni sulla visualizzazione della configurazione del DNS in Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 oppure Windows Server 2008 R2, fare clic sul pulsante **Start**, scegliere **Guida e supporto tecnico** e quindi cercare le **impostazioni di modifica TCP/IP**.  
  
- Per ulteriori informazioni, visitare il [sito Web Microsoft Windows](https://go.microsoft.com/fwlink/?LinkId=252720) e cercare le **impostazioni di modifica TCP/IP**.  
  
  Se è possibile risolvere il problema DNS, è possibile provare a eseguire il debugger remoto con un account diverso. L'errore si verifica quando è in esecuzione il debugger remoto con l'account del sistema locale o l'account del servizio di rete. Se si esegue il debugger remoto con un altro account, è possibile usare l'autenticazione NTLM, che non richiede il DNS. . Per la procedura, vedere [errore: il servizio Visual Studio Remote Debugger nel computer di destinazione non è in grado di riconnettersi a questo computer](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
