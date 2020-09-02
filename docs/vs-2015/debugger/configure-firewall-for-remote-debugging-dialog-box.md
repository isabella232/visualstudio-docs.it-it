---
title: Finestra di dialogo Configura firewall per debug remoto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26e2b1300feb8d2a15e63089ee9bddde5f2d1ef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702292"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Configura firewall per debug remoto (finestra di dialogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa finestra di dialogo viene visualizzata quando Windows Firewall impedisce al debugger di ricevere informazioni attraverso la rete. Per continuare il debug remoto, è necessario configurare un'apertura nel firewall per consentire al debugger di ricevere informazioni.  
  
> [!CAUTION]
> Se si configura un'apertura in Windows Firewall, il computer risulterà esposto a rischi per la sicurezza che normalmente verrebbero evitati grazie alla presenza del firewall. La configurazione di un'apertura per il debug remoto sblocca le porte 4020 e 4021 in Visual Studio 2015. In altre versioni di Visual Studio vengono usati altri numeri di porta. Per ulteriori informazioni, vedere [remote debugger Port assegnazioni](../debugger/remote-debugger-port-assignments.md). Il debugger ha inoltre la possibilità di aprire altre porte. Per altre informazioni, vedere [configurare la Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **Annulla debug remoto**  
 Annulla il tentativo di debug remoto. Le impostazioni di sicurezza del computer rimangono invariate.  
  
 **Sblocca debug remoto dai computer nella rete locale (subnet)**  
 Consente il debug remoto dei computer nella subnet locale. Questa impostazione può comportare rischi di sicurezza per i computer nella subnet locale, tuttavia il firewall continuerà a bloccare le informazioni provenienti dall'esterno della subnet.  
  
 **Sblocca debug remoto da qualunque computer**  
 Consente il debug remoto dei computer in qualsiasi area della rete. Questa impostazione comporta il maggior rischio di sicurezza.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Configurare il Strumenti remoti nel dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Riferimenti dell'interfaccia utente di debug](../debugger/debugging-user-interface-reference.md)
