---
title: "Procedura: disabilitare l'attivazione dell'URL delle applicazioni ClickOnce | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 75a98706858323693ec01ec3c3420a6d2d25ffef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697219"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Procedura: disabilitare l'attivazione dell'URL delle applicazioni ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In genere, un’applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] viene avviata automaticamente subito dopo l'installazione da un server Web. Per motivi legati alla sicurezza, è possibile disabilitare questo comportamento e invece indicare agli utenti di avviare l'applicazione dal menu **Start**. La procedura seguente descrive come disabilitare l’attivazione dell’URL.  
  
 Questa tecnica può essere usata solo per le applicazioni [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] installate nel computer dell'utente da un server Web. Non può essere usata per le applicazioni solo online, che possono essere avviate solo mediante l'URL. Per altre informazioni sulla differenza tra le applicazioni solo online e installate, vedere [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Questa procedura usa lo strumento MageUI.exe di [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Per altre informazioni su questo strumento, vedere [MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). È anche possibile eseguire questa procedura mediante [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Per disabilitare l'attivazione dell'URL per l'applicazione  
  
1. Aprire il manifesto della distribuzione in MageUI.exe. Se non è ancora stato creato, seguire i passaggi in [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2. Selezionare la scheda **Opzioni di distribuzione**.  
  
3. Deselezionare la casella di controllo **Esegui automaticamente l'applicazione dopo l'installazione**.  
  
4. Salvare e firmare il manifesto.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
