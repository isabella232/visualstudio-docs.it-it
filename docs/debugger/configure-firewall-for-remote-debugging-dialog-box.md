---
title: Finestra di dialogo Configura firewall per debug remoto | Microsoft Docs
description: Vedere la finestra di dialogo Configura firewall per debug remoto, che viene visualizzata quando il Windows Firewall interrompe la ricezione dei dati tramite la rete da parte del debugger.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 86a0cac2e42e1271e689f2b1880eef8ca6d14644
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728963"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Configura firewall per debug remoto (finestra di dialogo)
Questa finestra di dialogo viene visualizzata quando Windows Firewall impedisce al debugger di ricevere informazioni attraverso la rete. Per continuare il debug remoto, è necessario configurare un'apertura nel firewall per consentire al debugger di ricevere informazioni.

> [!CAUTION]
> Se si configura un'apertura in Windows Firewall, il computer risulterà esposto a rischi per la sicurezza che normalmente verrebbero evitati grazie alla presenza del firewall. La configurazione di un'apertura per il debug remoto sblocca le porte 4020 e 4021 in Visual Studio 2015. In altre versioni di Visual Studio vengono usati altri numeri di porta. Per ulteriori informazioni, vedere [remote debugger Port assegnazioni](../debugger/remote-debugger-port-assignments.md). Il debugger ha inoltre la possibilità di aprire altre porte. Per altre informazioni, vedere [configurare la Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Annulla debug remoto** Annulla il tentativo di debug remoto. Le impostazioni di sicurezza del computer rimangono invariate.

 **Sbloccare il debug remoto dai computer nella rete locale (subnet)** Consente il debug remoto dei computer nella subnet locale. Questa impostazione può comportare rischi di sicurezza per i computer nella subnet locale, tuttavia il firewall continuerà a bloccare le informazioni provenienti dall'esterno della subnet.

 **Sblocca debug remoto da qualsiasi computer** Consente il debug remoto di computer in qualsiasi punto della rete. Questa impostazione comporta il maggior rischio di sicurezza.

## <a name="see-also"></a>Vedi anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug remoto](../debugger/remote-debugging.md)
- [Riferimenti dell'interfaccia utente di debug](../debugger/debugging-user-interface-reference.md)