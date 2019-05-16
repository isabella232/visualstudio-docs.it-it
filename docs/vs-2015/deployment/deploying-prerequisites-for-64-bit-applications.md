---
title: Prerequisiti per le applicazioni a 64 bit la distribuzione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 92f30e8e059475c907da184aa59a8e4b7a2cf19f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675574"
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>Prerequisiti per la distribuzione di applicazioni a 64 bit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La distribuzione ClickOnce supporta l'installazione di applicazioni su piattaforme a 64 bit. Le piattaforme di destinazione sono **x86** per le piattaforme a 32 bit, **x64** per i computer che supportano i set di istruzioni AMD64 ed EM64T e **Itanium** per il processore Itanium a 64 bit.  
  
## <a name="prerequisites"></a>Prerequisiti  
 La tabella seguente elenca i componenti ridistribuibili che è possibile usare come prerequisiti per l'installazione dell'applicazione a 64 bit.  
  
 Se si seleziona un prerequisito che non ha componenti a 64 bit, è possibile che venga visualizzato un avviso che indica che i pacchetti selezionati non sono disponibili per la piattaforma a 64 bit.  
  
|Componente ridistribuibile|Supporto x64|Supporto IA64|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../includes/vsto-runtime-md.md)]|Yes|No|  
|Librerie di runtime di Visual C++ 2010 (IA64)|No|Yes|  
|Librerie di runtime di Visual C++ 2010 (x64)|Yes|No|  
|Microsoft .NET Framework 4 (x86 e x64)|Yes||  
|Microsoft .NET Framework 4 Client Profile (x86 e x64)|Yes||  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md)   
 [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Applicazioni a 64 bit](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)
