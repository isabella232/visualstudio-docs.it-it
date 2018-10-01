---
title: Prerequisiti per le applicazioni a 64 bit la distribuzione | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 0f98a611b382f3884ede2e1e239944b9e584ab77
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526837"
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>Prerequisiti per la distribuzione di applicazioni a 64 bit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [prerequisiti di distribuzione per le applicazioni a 64 bit](https://docs.microsoft.com/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications).  
  
La distribuzione ClickOnce supporta l'installazione di applicazioni su piattaforme a 64 bit. Le piattaforme di destinazione vengono **x86** per piattaforme a 32 bit **x64** per le macchine che supportano il set di istruzioni AMD64 ed EM64T, e **Itanium** per il processore Itanium a 64 bit.  
  
## <a name="prerequisites"></a>Prerequisiti  
 La tabella seguente elenca i componenti ridistribuibili che è possibile usare come prerequisiti per l'installazione dell'applicazione a 64 bit.  
  
 Se si seleziona un prerequisito che non ha componenti a 64 bit, è possibile che venga visualizzato un avviso che indica che i pacchetti selezionati non sono disponibili per la piattaforma a 64 bit.  
  
|Componente ridistribuibile|Supporto x64|Supporto IA64|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../includes/vsto-runtime-md.md)]|Sì|No|  
|Librerie di runtime di Visual C++ 2010 (IA64)|No|Sì|  
|Librerie di runtime di Visual C++ 2010 (x64)|Sì|No|  
|Microsoft .NET Framework 4 (x86 e x64)|Sì||  
|Microsoft .NET Framework 4 Client Profile (x86 e x64)|Yes||  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md)   
 [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Applicazioni a 64 bit](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)



