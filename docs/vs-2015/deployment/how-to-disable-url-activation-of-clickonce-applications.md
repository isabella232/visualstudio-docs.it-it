---
title: "Procedura: disabilitare l'attivazione dell'URL di applicazioni ClickOnce | Microsoft Docs"
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
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ad43abbafe1d5f70bb2de748154a0066aa3d8927
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525555"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Procedura: disabilitare l'attivazione dell'URL delle applicazioni ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: disabilitare l'attivazione URL di applicazioni di ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-disable-url-activation-of-clickonce-applications).  
  
In genere, un’applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] viene avviata automaticamente subito dopo l'installazione da un server Web. Per motivi di sicurezza, è possibile decidere di disattivare questo comportamento e comunicare agli utenti di avviare l'applicazione dal **avviare** menu invece. La procedura seguente descrive come disabilitare l’attivazione dell’URL.  
  
 Questa tecnica può essere usata solo per le applicazioni [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] installate nel computer dell'utente da un server Web. Non può essere usata per le applicazioni solo online, che possono essere avviate solo mediante l'URL. Per altre informazioni sulla differenza tra le applicazioni solo online e installate, vedere [scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Questa procedura usa lo strumento MageUI.exe di [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Per altre informazioni su questo strumento, vedere [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). È anche possibile eseguire questa procedura mediante [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="procedure"></a>Routine  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Per disabilitare l'attivazione dell'URL per l'applicazione  
  
1.  Aprire il manifesto della distribuzione in MageUI.exe. Se non ancora stato creato uno, seguire i passaggi descritti in [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Selezionare il **opzioni di distribuzione** scheda.  
  
3.  Cancella il **Esegui automaticamente l'applicazione dopo l'installazione** casella di controllo.  
  
4.  Salvare e firmare il manifesto.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)



