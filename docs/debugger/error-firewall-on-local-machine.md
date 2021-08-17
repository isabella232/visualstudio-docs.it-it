---
description: Nel computer locale, ovvero nel computer dal quale si esegue Visual Studio, Windows Firewall non è configurato in modo da consentire il debug remoto.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 17a5707c5b4d200b149b818ca321d85d41876146
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105223"
---
# <a name="error-firewall-on-local-machine"></a>Errore: firewall sul computer locale
Nel computer locale, ovvero nel computer dal quale si esegue Visual Studio, Windows Firewall non è configurato in modo da consentire il debug remoto. Per il debug remoto di codice gestito o nativo con il trasporto predefinito, è necessario aprire la porta TCP 135 per il traffico DCOM, nonché attivare la condivisione di file e stampanti e aggiungere devenv.exe all'elenco delle eccezioni. Potrebbe inoltre essere necessario aprire alcune porte IPSEC.

 Per altre informazioni, vedere [Debug remoto.](../debugger/remote-debugging.md)
