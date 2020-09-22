---
title: Firewall nel computer locale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 6b729c3e7e82a13d86aed16dfb52fda6864aa7f9
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852706"
---
# <a name="error-firewall-on-local-machine"></a>Errore: firewall sul computer locale
Nel computer locale, ovvero nel computer dal quale si esegue Visual Studio, Windows Firewall non è configurato in modo da consentire il debug remoto. Per il debug remoto di codice gestito o nativo con il trasporto predefinito, è necessario aprire la porta TCP 135 per il traffico DCOM, nonché attivare la condivisione di file e stampanti e aggiungere devenv.exe all'elenco delle eccezioni. Potrebbe inoltre essere necessario aprire alcune porte IPSEC.

 Per ulteriori informazioni, vedere [Remote Debugging](../debugger/remote-debugging.md).