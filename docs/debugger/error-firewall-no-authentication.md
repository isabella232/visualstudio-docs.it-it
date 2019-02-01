---
title: 'Errore: Nessuna autenticazione del firewall | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.noauth
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
ms.openlocfilehash: e565d1372131272f8653df328dbbe9749a8b1ddb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035302"
---
# <a name="error-firewall-no-authentication"></a>Errore: Nessuna autenticazione del firewall
Nel computer remoto Windows Firewall non è configurato in modo da consentire il debug remoto. Per il debug remoto con `No Authentication` è necessario aggiungere msvsmon.exe all'elenco delle eccezioni. Potrebbe inoltre essere necessario aprire alcune porte IPSEC.  
  
> [!NOTE]
>  Il debugger remoto esegue automaticamente la configurazione di Windows Firewall. Quando si utilizza un firewall diverso da Windows Firewall, ad esempio un firewall hardware o software di terze parti, è necessario configurarlo manualmente per consentire il debug remoto. A tale scopo, consentire il traffico sulle porte TCP/IP su cui msvsmon.exe è in ascolto. Per impostazione predefinita, si tratta delle porte 4018 e 4019, dove la 4018 è utilizzata in tutti i sistemi operativi e la 4019 è utilizzata solo in Windows x64 per consentire i processi di debug x86.  
  
 Per altre informazioni, vedere [debug remoto](../debugger/remote-debugging.md).