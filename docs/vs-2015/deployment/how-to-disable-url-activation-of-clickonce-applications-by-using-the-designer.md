---
title: "Procedura: disabilitare l'attivazione dell'URL di applicazioni ClickOnce tramite la finestra di progettazione | Microsoft Docs"
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
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 6cc5571dffba9daa3ac1f5f78e354487cbc654fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526792"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Procedura: disabilitare gli URL di applicazioni ClickOnce tramite la finestra di progettazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: disabilitare URL di attivazione di applicazioni ClickOnce tramite la finestra di progettazione](https://docs.microsoft.com/visualstudio/deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer).  
  
In genere, un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione verrà avviata automaticamente subito dopo l'installazione da un server Web. Per motivi di sicurezza, è possibile decidere di disattivare questo comportamento e comunicare agli utenti di avviare l'applicazione dal **avviare** menu invece. La procedura seguente descrive come disabilitare l’attivazione dell’URL.  
  
 Questa tecnica può essere usata solo per le applicazioni [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] installate nel computer dell'utente da un server Web. Non è utilizzabile per le applicazioni solo online, che possono essere avviate solo tramite i rispettivi URL. Per altre informazioni sulla differenza tra le applicazioni solo online e installate, vedere [scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Questa procedura Usa [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. È inoltre possibile eseguire questa attività usando il [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Per altre informazioni, vedere [procedura: disabilitare l'attivazione URL di applicazioni di ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Routine  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Per disabilitare l'attivazione dell'URL per l'applicazione  
  
1.  Fare clic sul nome del progetto in **Esplora soluzioni**, fare clic su **proprietà**.  
  
2.  Nel **delle proprietà** pagina, fare clic sul **pubblica** scheda.  
  
3.  Fare clic su **Opzioni**.  
  
4.  Fare clic su **manifesti**.  
  
5.  Selezionare la casella di controllo etichettata **blocco applicazione venga attivata tramite un URL**.  
  
6.  Distribuire l'applicazione,  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)



