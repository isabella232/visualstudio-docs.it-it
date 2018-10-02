---
title: 'Errore: Nessuna autenticazione del Firewall | Microsoft Docs'
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
- vs.debug.error.firewall.noauth
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: dda1acb8-bed7-4bc8-9991-9cdc49c2ac1e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dca0d4421cb8b8b5e720ca079547f13ec75e3705
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526011"
---
# <a name="error-firewall-no-authentication"></a>Errore: nessuna autenticazione del firewall
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [errore: Firewall Nessuna autenticazione](https://docs.microsoft.com/visualstudio/debugger/error-firewall-no-authentication).  
  
Nel computer remoto Windows Firewall non è configurato in modo da consentire il debug remoto. Per il debug remoto con `No Authentication` è necessario aggiungere msvsmon.exe all'elenco delle eccezioni. Potrebbe inoltre essere necessario aprire alcune porte IPSEC.  
  
> [!NOTE]
>  Il debugger remoto esegue automaticamente la configurazione di Windows Firewall. Quando si utilizza un firewall diverso da Windows Firewall, ad esempio un firewall hardware o software di terze parti, è necessario configurarlo manualmente per consentire il debug remoto. A tale scopo, consentire il traffico sulle porte TCP/IP su cui msvsmon.exe è in ascolto. Per impostazione predefinita, si tratta delle porte 4018 e 4019, dove la 4018 è utilizzata in tutti i sistemi operativi e la 4019 è utilizzata solo in Windows x64 per consentire i processi di debug x86.  
  
 Per altre informazioni, vedere [Set Up the Remote Tools sul dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).



