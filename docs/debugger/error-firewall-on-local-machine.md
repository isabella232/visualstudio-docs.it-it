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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5f3e57bbac1d2c293c5a9f910beca5484db06cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871593"
---
# <a name="error-firewall-on-local-machine"></a>Errore: firewall sul computer locale
Nel computer locale, ovvero nel computer dal quale si esegue Visual Studio, Windows Firewall non è configurato in modo da consentire il debug remoto. Per il debug remoto di codice gestito o nativo con il trasporto predefinito, è necessario aprire la porta TCP 135 per il traffico DCOM, nonché attivare la condivisione di file e stampanti e aggiungere devenv.exe all'elenco delle eccezioni. Potrebbe inoltre essere necessario aprire alcune porte IPSEC.

 Per ulteriori informazioni, vedere [Remote Debugging](../debugger/remote-debugging.md).