---
title: 'Debug della preparazione: Applicazioni Web ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging ASP.NET Web applications
- debugging [Visual Studio], Web applications
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e7a2640d39c90dc36a3960d230df46ac75bdbce6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092422"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Debug della preparazione: Applicazioni Web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]modello sito Web consente di creare un'applicazione Web Form. Quando si crea un sito Web mediante questo modello, in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vengono definite automaticamente le impostazioni predefinite per il debug. Nel **proprietà del progetto** nella finestra di dialogo è possibile specificare se si desidera che la pagina Web da una pagina di avvio. Quando si avvia il debug di un' [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]sito Web con queste impostazioni predefinite, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] avvia Internet Explorer e collega il debugger per il [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] processo di lavoro (aspnet_wp.exe o w3wp.exe). Per altre informazioni, vedere [System Requirements](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>Per creare un'applicazione Web Form  
  
1. Nel **File** menu, scegliere **nuovo sito Web**.  
  
2. Nel **nuovo sito Web** finestra di dialogo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **sito Web**.  
  
3. Fare clic su **OK**.  
  
### <a name="to-debug-your-web-form"></a>Per eseguire il debug del Web Form  
  
1. Impostare uno o più punti di interruzione nelle funzioni e nei gestori eventi.  
  
     Per altre informazioni, vedere [Breakpoints and Tracepoints](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. Quando viene raggiunto un punto di interruzione, eseguire il codice un'istruzione alla volta all'interno della funzione. Osservare l'esecuzione del codice finché non si individua il problema.  
  
     Per altre informazioni, vedere [esecuzione di istruzioni](http://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) e [Script e il debug di applicazioni Web](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Modifica delle configurazioni predefinite  
 Se si desidera, è possibile modificare le configurazioni di debug e di rilascio predefinite create da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per altre informazioni, vedere [Procedura: Impostare configurazioni di debug e di rilascio](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>Per modificare la configurazione di debug predefinita  
  
1. Nelle **Esplora soluzioni**, il sito Web e scegliere **pagine delle proprietà** per aprire il **pagine delle proprietà** nella finestra di dialogo.  
  
2. Fare clic su **opzioni di avvio**.  
  
3. Impostare **azione di avvio** alla pagina Web che devono essere visualizzata per primi.  
  
4. Sotto **debugger**, assicurarsi che **debug ASP.NET** sia selezionata.  
  
     Per altre informazioni, vedere [le impostazioni delle pagine delle proprietà per i progetti Web](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debugger Settings and Preparation](../debugger/debugger-settings-and-preparation.md)  (Impostazioni di debug e preparazione)  
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug di codice gestito](../debugger/debugging-managed-code.md)
