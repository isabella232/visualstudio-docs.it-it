---
title: Prerequisiti per il debug di applicazioni Web remoto | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 197a6e9b433173f1de13e3506db79e7edf53bade
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527111"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Prerequisiti per il debug remoto di applicazioni Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [prerequisiti per Remote Debug delle applicazioni Web](https://docs.microsoft.com/visualstudio/debugger/prerequistes-for-remote-debugging-web-applications).  
  
Il debugger [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consente di eseguire il debug di un'applicazione Web in modo trasparente nel computer locale o in un server remoto. Il debugger funziona nello stesso modo e consente di utilizzare le stesse funzionalità in entrambi i computer. Esistono tuttavia alcuni prerequisiti per la corretta esecuzione del debug remoto.  
  
-   I componenti per il debug remoto di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] devono essere installati nel server di cui si desidera eseguire il debug. Per altre informazioni, vedere [impostazione del debug remoto](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
-   Per impostazione predefinita, il processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] viene eseguito come processo utente ASPNET. Di conseguenza, per eseguire il debug è necessario disporre dei privilegi di amministratore per il computer in cui viene eseguito [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Il nome del processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] varia in base allo scenario di debug e alla versione di IIS. Per altre informazioni, vedere [How to: Find the Name of the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md)



