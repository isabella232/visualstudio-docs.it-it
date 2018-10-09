---
title: 'Preparazione al debug: Applicazioni Web ASP.NET | Microsoft Docs'
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
- VB
- CSharp
helpviewer_keywords:
- debugging ASP.NET Web applications
- debugging [Visual Studio], Web applications
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20731f5036a89c3c19fbea0d825d67fc02c13cf9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528714"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Preparazione al debug: applicazioni Web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [preparazione al debug: applicazioni Web ASP.NET](https://docs.microsoft.com/visualstudio/debugger/debugging-preparation-aspnet-web-applications).  
  
Il [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]modello sito Web consente di creare un'applicazione Web Form. Quando si crea un sito Web mediante questo modello, in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vengono definite automaticamente le impostazioni predefinite per il debug. Nel **proprietà del progetto** nella finestra di dialogo è possibile specificare se si desidera che la pagina Web da una pagina di avvio. Quando si avvia il debug di un' [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]sito Web con queste impostazioni predefinite, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] avvia Internet Explorer e collega il debugger per il [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] processo di lavoro (aspnet_wp.exe o w3wp.exe). Per altre informazioni, vedere [requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>Per creare un'applicazione Web Form  
  
1.  Nel **File** menu, scegliere **nuovo sito Web**.  
  
2.  Nel **nuovo sito Web** finestra di dialogo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **sito Web**.  
  
3.  Fare clic su **OK**.  
  
### <a name="to-debug-your-web-form"></a>Per eseguire il debug del Web Form  
  
1.  Impostare uno o più punti di interruzione nelle funzioni e nei gestori eventi.  
  
     Per altre informazioni, vedere [Breakpoints and Tracepoints](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Quando viene raggiunto un punto di interruzione, eseguire il codice un'istruzione alla volta all'interno della funzione. Osservare l'esecuzione del codice finché non si individua il problema.  
  
     Per altre informazioni, vedere [esecuzione di istruzioni](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9) e [Script e il debug di applicazioni Web](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Modifica delle configurazioni predefinite  
 Se si desidera, è possibile modificare le configurazioni di debug e di rilascio predefinite create da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per altre informazioni, vedere [Procedura: Impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>Per modificare la configurazione di debug predefinita  
  
1.  Nelle **Esplora soluzioni**, il sito Web e scegliere **pagine delle proprietà** per aprire il **pagine delle proprietà** nella finestra di dialogo.  
  
2.  Fare clic su **opzioni di avvio**.  
  
3.  Impostare **azione di avvio** alla pagina Web che devono essere visualizzata per primi.  
  
4.  Sotto **debugger**, assicurarsi che **debug ASP.NET** sia selezionata.  
  
     Per altre informazioni, vedere [le impostazioni delle pagine delle proprietà per i progetti Web](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debugger Settings and Preparation](../debugger/debugger-settings-and-preparation.md)  (Impostazioni di debug e preparazione)  
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug di codice gestito](../debugger/debugging-managed-code.md)


