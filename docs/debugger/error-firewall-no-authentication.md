---
description: Nel computer remoto Windows Firewall non è configurato in modo da consentire il debug remoto.
title: Nessuna autenticazione del firewall | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7e42a9dd2856c9bee14b480b261231932dc30236
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030953"
---
# <a name="error-firewall-no-authentication"></a>Errore: nessuna autenticazione del firewall
Nel computer remoto Windows Firewall non è configurato in modo da consentire il debug remoto. Per il debug remoto con `No Authentication` è necessario aggiungere msvsmon.exe all'elenco delle eccezioni. Potrebbe inoltre essere necessario aprire alcune porte IPSEC.

> [!NOTE]
> Il debugger remoto esegue automaticamente la configurazione di Windows Firewall. Quando si utilizza un firewall diverso da Windows Firewall, ad esempio un firewall hardware o software di terze parti, è necessario configurarlo manualmente per consentire il debug remoto. A tale scopo, consentire il traffico sulle porte TCP/IP su cui msvsmon.exe è in ascolto. Per impostazione predefinita, si tratta delle porte 4018 e 4019, dove la 4018 è utilizzata in tutti i sistemi operativi e la 4019 è utilizzata solo in Windows x64 per consentire i processi di debug x86.

 Per altre informazioni, vedere [Debug remoto.](../debugger/remote-debugging.md)
