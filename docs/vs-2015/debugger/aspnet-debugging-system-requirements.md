---
title: 'Debug ASP.NET: Requisiti di sistema | Microsoft Docs'
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
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aa8951be6da4d77ffb51b6bc8f09a796b373a944
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67826252"
---
# <a name="aspnet-debugging-system-requirements"></a>Debug ASP.NET: Requisiti di sistema
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento vengono descritti i requisiti software e di sicurezza per gli scenari di debug di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] :  
  
- Debug locale in cui [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e l'applicazione Web vengono eseguiti nello stesso computer. Questo scenario presenta due varianti:  
  
  - Il codice [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] risiede nel file system.  

  - Il codice [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] risiede in un sito Web IIS.  
  
- Il debug remoto in cui [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] è in esecuzione in un computer client ed esegue il debug di un'applicazione Web in esecuzione in un computer server remoto.  
  
## <a name="security-requirements"></a>Requisiti di sicurezza  
 Per il debug remoto, i computer locale e remoto devono appartenere a una configurazione di dominio o di gruppo di lavoro.  
  
 Per eseguire il debug del processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , è necessario disporre delle autorizzazioni appropriate. Per impostazione predefinita, le applicazioni [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] vengono eseguite come utente **ASPNET** . Se il processo di lavoro è in esecuzione come **ASPNET**o come **SERVIZIO DI RETE**, per eseguirne il debug è necessario disporre dei privilegi di amministratore.  
  
 Il nome del processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] varia in base allo scenario di debug e alla versione di IIS. Per altre informazioni, vedere [Procedura: Trovare il nome del processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 È possibile modificare l'account utente con cui il processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] viene eseguito modificando il file machine.config nel server su cui è in esecuzione IIS. Il modo migliore per eseguire questa operazione è usare **Gestione Internet Information Services (IIS)** . Per altre informazioni, vedere [Procedura: Eseguire il processo di lavoro con un account utente](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Se si modifica il processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] affinché venga eseguito con il proprio account utente, non è necessario essere un amministratore nel server che esegue IIS.  
  
> [!CAUTION]
> Prima di modificare il processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] in modo che venga eseguito con un account diverso, considerare le possibili conseguenze di un eventuale attacco al processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] mentre viene eseguito con tale account. Gli account utente ASPNET e SERVIZIO DI RETE vengono eseguiti con autorizzazioni minime, riducendo il più possibile i danni in caso di attacchi al processo. Se è necessario modificare il processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] in modo che venga eseguito con un account con autorizzazioni più elevate, il danno potenziale è maggiore.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Procedura: Eseguire il processo di lavoro con un account utente](../debugger/how-to-run-the-worker-process-under-a-user-account.md)
