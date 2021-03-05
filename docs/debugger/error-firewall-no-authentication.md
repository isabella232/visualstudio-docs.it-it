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
ms.workload:
- multiple
ms.openlocfilehash: 2bb46b09af4f87ac93fd7001ff1de02a782ae263
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146990"
---
# <a name="error-firewall-no-authentication"></a>Errore: nessuna autenticazione del firewall
Nel computer remoto Windows Firewall non è configurato in modo da consentire il debug remoto. Per il debug remoto con `No Authentication` è necessario aggiungere msvsmon.exe all'elenco delle eccezioni. Potrebbe inoltre essere necessario aprire alcune porte IPSEC.

> [!NOTE]
> Il debugger remoto esegue automaticamente la configurazione di Windows Firewall. Quando si utilizza un firewall diverso da Windows Firewall, ad esempio un firewall hardware o software di terze parti, è necessario configurarlo manualmente per consentire il debug remoto. A tale scopo, consentire il traffico sulle porte TCP/IP su cui msvsmon.exe è in ascolto. Per impostazione predefinita, si tratta delle porte 4018 e 4019, dove la 4018 è utilizzata in tutti i sistemi operativi e la 4019 è utilizzata solo in Windows x64 per consentire i processi di debug x86.

 Per ulteriori informazioni, vedere [Remote Debugging](../debugger/remote-debugging.md).
