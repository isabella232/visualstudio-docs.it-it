---
title: Configurare il Firewall per la finestra di dialogo di debug remoto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75342630e347eaabe6854498c43294599afae5a5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637516"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Configura firewall per debug remoto (finestra di dialogo)
Questa finestra di dialogo viene visualizzata quando Windows Firewall impedisce al debugger di ricevere informazioni attraverso la rete. Per continuare il debug remoto, è necessario configurare un'apertura nel firewall per consentire al debugger di ricevere informazioni.

> [!CAUTION]
> Se si configura un'apertura in Windows Firewall, il computer risulterà esposto a rischi per la sicurezza che normalmente verrebbero evitati grazie alla presenza del firewall. La configurazione di un'apertura per il debug remoto sblocca le porte 4020 e 4021 in Visual Studio 2015. In altre versioni di Visual Studio vengono usati altri numeri di porta. Per altre informazioni, vedere [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Il debugger ha inoltre la possibilità di aprire altre porte. Per altre informazioni, vedere [configurare il Firewall di Windows per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="uielement-list"></a>Elenco UIElement
 **Annulla debug remoto** Annulla il tentativo di debug remoto. Le impostazioni di sicurezza del computer rimangono invariate.

 **Sblocca debug remoto dai computer nella rete locale (subnet)** Abilita debug remoto dei computer sulla subnet locale. Questa impostazione può comportare rischi di sicurezza per i computer nella subnet locale, tuttavia il firewall continuerà a bloccare le informazioni provenienti dall'esterno della subnet.

 **Sblocca debug remoto da qualsiasi computer** Abilita debug remoto dei computer in un punto qualsiasi nella rete. Questa impostazione comporta il maggior rischio di sicurezza.

## <a name="see-also"></a>Vedere anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Remote Debugging](../debugger/remote-debugging.md)
- [Riferimenti dell'interfaccia utente di debug](../debugger/debugging-user-interface-reference.md)