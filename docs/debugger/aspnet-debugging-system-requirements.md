---
title: 'ASP.NET Debug: requisiti di sistema | Microsoft Docs'
description: Esaminare i requisiti software e di sicurezza ASP.NET debug locale, in cui Visual Studio e l'app Web vengono eseguiti nello stesso computer e il debug remoto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: 6de11302ea67e27e46348638701172abc5e0964b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630965"
---
# <a name="aspnet-debugging-system-requirements"></a>Requisiti di sistema per il debug di ASP.NET
In questo argomento vengono descritti i requisiti software e di sicurezza per gli scenari di debug di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] :

- Debug locale in cui [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e l'applicazione Web vengono eseguiti nello stesso computer. Questo scenario presenta due varianti:

  - Il codice [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] risiede nel file system.

  - Il codice [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] risiede in un sito Web IIS.

- Il debug remoto in cui [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è in esecuzione in un computer client ed esegue il debug di un'applicazione Web in esecuzione in un computer server remoto.

## <a name="security-requirements"></a>Requisiti di sicurezza
 Per il debug remoto, i computer locale e remoto devono appartenere a una configurazione di dominio o di gruppo di lavoro.

 Per eseguire il [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] debug del processo di lavoro (ospitato da un pool di applicazioni), è necessario disporre dell'autorizzazione per eseguire il debug di tale processo. Per impostazione predefinita, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] le applicazioni precedenti a IIS 6.0 vengono eseguite come utente **ASPNET.** In IIS 6.0 e IIS 7.0 l'account **NETWORK SERVICE** è l'impostazione predefinita. Se il processo di lavoro è in esecuzione come **ASPNET** o come **SERVIZIO DI RETE**, per eseguirne il debug è necessario disporre dei privilegi di amministratore.

 > [!IMPORTANT]
 > A partire da Windows Server 2008 R2, è consigliabile usare [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) come identità per ogni pool di applicazioni.

 Il nome del processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] varia in base allo scenario di debug e alla versione di IIS. Per altre informazioni, vedere [Procedura: individuare il nome del processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).

 È possibile modificare l'account utente con cui il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] viene eseguito modificando il file machine.config nel server su cui è in esecuzione IIS. Il modo migliore per eseguire questa operazione è usare **Gestione Internet Information Services (IIS)**. Per altre informazioni, vedere [Procedura: Eseguire il processo di lavoro con un account utente.](../debugger/how-to-run-the-worker-process-under-a-user-account.md)

 Se si modifica il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] affinché venga eseguito con il proprio account utente, non è necessario essere un amministratore nel server che esegue IIS.

> [!CAUTION]
> Prima di modificare il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in modo che venga eseguito con un account diverso, considerare le possibili conseguenze di un eventuale attacco al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] mentre viene eseguito con tale account. Gli account utente ASPNET e SERVIZIO DI RETE vengono eseguiti con autorizzazioni minime, riducendo il più possibile i danni in caso di attacchi al processo. Se è necessario modificare il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in modo che venga eseguito con un account con autorizzazioni più elevate, il danno potenziale è maggiore.

## <a name="see-also"></a>Vedi anche

- [Eseguire il debug ASP.NET applicazioni](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Procedura: Eseguire il processo di lavoro con un account utente](../debugger/how-to-run-the-worker-process-under-a-user-account.md)