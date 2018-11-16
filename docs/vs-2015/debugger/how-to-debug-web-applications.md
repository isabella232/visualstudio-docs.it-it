---
title: 'Procedura: eseguire il Debug di applicazioni Web | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2a5110a6801aafb6eaf98cb4fb4164b045b2408
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793633"
---
# <a name="how-to-debug-web-applications"></a>Procedura: eseguire il debug di applicazioni Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] è la tecnologia principale per lo sviluppo di applicazioni Web in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Il debugger di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornisce potenti strumenti per il debug di applicazioni Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] a livello locale o su un server remoto. Questo argomento descrive come eseguire il debug di un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] progetto durante lo sviluppo. Per informazioni su come eseguire il debug di un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] già distribuito in un server di produzione di applicazioni Web, vedere [il debug di applicazioni Web distribuite](../debugger/debugging-deployed-web-applications.md).  
  
 Per eseguire il debug di un'applicazione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]:  
  
-   È necessario disporre delle autorizzazioni richieste. Per altre informazioni, vedere [System Requirements](../debugger/aspnet-debugging-system-requirements.md).  
  
-   [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] il debug deve essere abilitato nel **proprietà del progetto**.  
  
-   Il file di configurazione dell'applicazione (Web.config) deve essere impostato sulla modalità debug. La modalità di debug fa in modo che [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] generi simboli per i file generati dinamicamente e consente al debugger di creare un allegato all'applicazione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] configura automaticamente questa impostazione quando si avvia il debug, se il progetto è stato creato dal modello dei progetti Web.  
  
-   Per altre informazioni, vedere [procedura: attivare il debug per le applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### <a name="to-debug-a-web-application-during-development"></a>Per eseguire il debug di un'applicazione Web durante lo sviluppo  
  
1.  Nel **Debug** menu, fare clic su **avviare** per avviare il debug dell'applicazione Web.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] compila il progetto applicazione Web, distribuisce l'applicazione se necessario, avvia il server di sviluppo ASP.NET se il debug viene eseguito a livello locale e si connette al processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
2.  Utilizzare il debugger  per impostare e rimuovere punti di interruzione, eseguire singole istruzioni e compiere altre operazioni di debug, come per qualsiasi altra applicazione.  
  
     Per altre informazioni, vedere [nozioni fondamentali di debug](../debugger/debugger-basics.md).  
  
3.  Nel **eseguire il Debug** menu, fare clic su **arresta debug** alla fine della sessione di debug o, nel **File** dal menu in Internet Explorer, fare clic su **Chiudi**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di script e applicazioni Web](../debugger/debugging-web-applications-and-script.md)   
 [Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Procedura: Attivare il debug per applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)



