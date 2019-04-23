---
title: Prerequisiti per il debug di applicazioni Web remoto | Microsoft Docs
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
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46bf49567558cab556180c470bfd4b80d93f5dbb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105513"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Prerequisiti per il debug remoto di applicazioni Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debugger [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consente di eseguire il debug di un'applicazione Web in modo trasparente nel computer locale o in un server remoto. Il debugger funziona nello stesso modo e consente di utilizzare le stesse funzionalità in entrambi i computer. Esistono tuttavia alcuni prerequisiti per la corretta esecuzione del debug remoto.  
  
- I componenti per il debug remoto di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] devono essere installati nel server di cui si desidera eseguire il debug. Per altre informazioni, vedere [impostazione del debug remoto](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
- Per impostazione predefinita, il processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] viene eseguito come processo utente ASPNET. Di conseguenza, per eseguire il debug è necessario disporre dei privilegi di amministratore per il computer in cui viene eseguito [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Il nome del processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] varia in base allo scenario di debug e alla versione di IIS. Per altre informazioni, vedere [Procedura: Trovare il nome del processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md)
