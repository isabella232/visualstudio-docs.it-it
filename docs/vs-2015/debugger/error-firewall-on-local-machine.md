---
title: 'Errore: Firewall sul computer locale | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3dfc0d216cc205f00e4c0df0bd62f86173379922
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728632"
---
# <a name="error-firewall-on-local-machine"></a>Errore: firewall sul computer locale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nel computer locale, ovvero nel computer dal quale si esegue Visual Studio, Windows Firewall non è configurato in modo da consentire il debug remoto. Per il debug remoto di codice gestito o nativo con il trasporto predefinito, è necessario aprire la porta TCP 135 per il traffico DCOM, nonché attivare la condivisione di file e stampanti e aggiungere devenv.exe all'elenco delle eccezioni. Potrebbe inoltre essere necessario aprire alcune porte IPSEC.  
  
 Per altre informazioni, vedere [Set Up the Remote Tools sul dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).



