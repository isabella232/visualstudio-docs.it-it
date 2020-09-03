---
title: 'Procedura: eseguire il debug di applicazioni Web | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: cd3cbbcd740c0f124b8ab4379204a9d425cd541c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205408"
---
# <a name="how-to-debug-web-applications"></a>Procedura: eseguire il debug di applicazioni Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] è la tecnologia principale per lo sviluppo di applicazioni Web in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Il debugger di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornisce potenti strumenti per il debug di applicazioni Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] a livello locale o su un server remoto. In questo argomento viene descritto come eseguire il debug di un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] progetto durante lo sviluppo. Per informazioni su come eseguire il debug di un' [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] applicazione Web già distribuita in un server di produzione, vedere [debug di applicazioni Web distribuite](../debugger/debugging-deployed-web-applications.md).  
  
 Per eseguire il debug di un'applicazione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]:  
  
- È necessario disporre delle autorizzazioni richieste. Per altre informazioni, vedere [System Requirements](../debugger/aspnet-debugging-system-requirements.md).  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] il debug deve essere abilitato nelle **proprietà del progetto**.  
  
- Il file di configurazione dell'applicazione (Web.config) deve essere impostato sulla modalità debug. La modalità di debug fa in modo che [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] generi simboli per i file generati dinamicamente e consente al debugger di creare un allegato all'applicazione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] configura automaticamente questa impostazione quando si avvia il debug, se il progetto è stato creato dal modello dei progetti Web.  
  
- Per altre informazioni, vedere [procedura: abilitare il debug per le applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### <a name="to-debug-a-web-application-during-development"></a>Per eseguire il debug di un'applicazione Web durante lo sviluppo  
  
1. Scegliere **Avvia** dal menu **debug** per avviare il debug dell'applicazione Web.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Compila il progetto di applicazione Web, distribuisce l'applicazione, se necessario, avvia il Server di sviluppo ASP.NET se si esegue il debug in locale e si connette al [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] processo di lavoro.  
  
2. Utilizzare il debugger  per impostare e rimuovere punti di interruzione, eseguire singole istruzioni e compiere altre operazioni di debug, come per qualsiasi altra applicazione.  
  
     Per ulteriori informazioni, vedere [nozioni di base sul debugger](../debugger/debugger-basics.md).  
  
3. Scegliere Termina **debug** dal menu **debug** per terminare la sessione di debug oppure scegliere **Chiudi**dal menu **file** in Internet Explorer.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di script e applicazioni Web](../debugger/debugging-web-applications-and-script.md)   
 [Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Come fare per: Attivare il debug per applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
