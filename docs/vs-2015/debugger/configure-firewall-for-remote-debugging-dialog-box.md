---
title: Configurare il Firewall per la finestra di dialogo di debug remoto | Microsoft Docs
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
- vs.debug.firewallconfiguration
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26e53e4573de1fb80d33b387e97b6ddd23b54bbb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540846"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Configura firewall per debug remoto (finestra di dialogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Configura Firewall per la finestra di dialogo di debug remoto](https://docs.microsoft.com/visualstudio/debugger/configure-firewall-for-remote-debugging-dialog-box).  
  
Questa finestra di dialogo viene visualizzata quando Windows Firewall impedisce al debugger di ricevere informazioni attraverso la rete. Per continuare il debug remoto, è necessario configurare un'apertura nel firewall per consentire al debugger di ricevere informazioni.  
  
> [!CAUTION]
>  Se si configura un'apertura in Windows Firewall, il computer risulterà esposto a rischi per la sicurezza che normalmente verrebbero evitati grazie alla presenza del firewall. La configurazione di un'apertura per il debug remoto sblocca le porte 4020 e 4021 in Visual Studio 2015. In altre versioni di Visual Studio vengono usati altri numeri di porta. Per altre informazioni, vedere [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Il debugger ha inoltre la possibilità di aprire altre porte. Per altre informazioni, vedere [configurare il Firewall di Windows per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Annulla debug remoto**  
 Annulla il tentativo di debug remoto. Le impostazioni di sicurezza del computer rimangono invariate.  
  
 **Sblocca debug remoto dai computer nella rete locale (subnet)**  
 Consente il debug remoto dei computer nella subnet locale. Questa impostazione può comportare rischi di sicurezza per i computer nella subnet locale, tuttavia il firewall continuerà a bloccare le informazioni provenienti dall'esterno della subnet.  
  
 **Sblocca debug remoto da qualsiasi computer**  
 Consente il debug remoto dei computer in qualsiasi area della rete. Questa impostazione comporta il maggior rischio di sicurezza.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Impostare Remote Tools sul dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Riferimenti dell'interfaccia utente di debug](../debugger/debugging-user-interface-reference.md)



