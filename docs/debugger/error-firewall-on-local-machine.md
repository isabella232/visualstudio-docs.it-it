---
title: 'Errore: Firewall sul computer locale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.localmachine
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
ms.openlocfilehash: 1781fef79dc9d80bae6a0484788298324e8bbd52
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963736"
---
# <a name="error-firewall-on-local-machine"></a>Errore: Firewall sul computer locale
Nel computer locale, ovvero nel computer dal quale si esegue Visual Studio, Windows Firewall non è configurato in modo da consentire il debug remoto. Per il debug remoto di codice gestito o nativo con il trasporto predefinito, è necessario aprire la porta TCP 135 per il traffico DCOM, nonché attivare la condivisione di file e stampanti e aggiungere devenv.exe all'elenco delle eccezioni. Potrebbe inoltre essere necessario aprire alcune porte IPSEC.  
  
 Per altre informazioni, vedere [debug remoto](../debugger/remote-debugging.md).