---
title: 'Procedura: eseguire il Debug di un servizio WCF Self-Hosted | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 255ca0f7d472060d110135536d76de99dc46a18e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872122"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Procedura: eseguire il debug di un servizio WCF indipendente
Oggetto *servizio indipendente* è un servizio WCF che non viene eseguito in IIS, l'Host del servizio WCF o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server. Il modo più semplice per eseguire il debug di un servizio WCF indipendente consiste nel configurare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per avviare client e server quando si sceglie **Avvia debug** sul **Debug** menu.  
  
 Se il servizio WCF è Self-hosting interno o un processo che non può essere avviato in questo modo, ad esempio servizio NT, è possibile utilizzare questo metodo. In alternativa, è possibile eseguire una delle operazioni seguenti:  
  
-   Collegare manualmente il debugger al processo di hosting. Per altre informazioni, vedere [connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     oppure  
  
-   Avviare il debug di client e quindi eseguire una chiamata al servizio. Ciò richiede l'abilitazione del debug nel file app. config. Per altre informazioni, [limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Per avviare l'host sia il client da Visual Studio  
  
1. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione contenente progetti sia il client e server.  
  
2. Configurare la soluzione per avviare i processi client e server quando si sceglie **avviare** nel **Debug** menu.  
  
   1.  Nelle **Esplora soluzioni**, fare clic sul nome della soluzione.  
  
   2.  Fare clic su **Imposta progetti di avvio**.  
  
   3.  Nel **soluzione \<nome > proprietà** nella finestra di dialogo **progetti di avvio multipli**.  
  
   4.  Nel **progetti di avvio multipli** griglia, nella riga che corrisponde al progetto server, fare clic su **azione** e scegliere **avviare**.  
  
   5.  Nella riga che corrisponde al progetto client, fare clic su **azione** e scegliere **avviare**.  
  
   6.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug dei servizi WCF](../debugger/debugging-wcf-services.md)   
 [Limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Procedura: Eseguire istruzioni nei servizi WCF](../debugger/how-to-step-into-wcf-services.md)