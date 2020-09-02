---
title: 'Preparazione al debug: applicazioni Web ASP.NET | Microsoft Docs'
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
ms.openlocfilehash: 7a80587062442688551d07128a2cec49a712adf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691454"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Preparazione al debug: applicazioni Web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] modello di sito Web crea un'applicazione Web Form. Quando si crea un sito Web mediante questo modello, in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vengono definite automaticamente le impostazioni predefinite per il debug. Nella finestra di dialogo **Proprietà progetto** è possibile specificare se si desidera che la pagina Web sia una pagina di avvio. Quando si avvia il debug [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] di un sito Web con queste impostazioni predefinite, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] avvia Internet Explorer e collega il debugger al [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] processo di lavoro (aspnet_wp.exe o w3wp.exe). Per altre informazioni, vedere [System Requirements](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>Per creare un'applicazione Web Form  
  
1. Scegliere **nuovo sito Web**dal menu **file** .  
  
2. Nella finestra di dialogo **nuovo sito Web** selezionare [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **sito Web**.  
  
3. Fare clic su **OK**.  
  
### <a name="to-debug-your-web-form"></a>Per eseguire il debug del Web Form  
  
1. Impostare uno o più punti di interruzione nelle funzioni e nei gestori eventi.  
  
     Per altre informazioni, vedere [Breakpoints and Tracepoints](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. Quando viene raggiunto un punto di interruzione, eseguire il codice un'istruzione alla volta all'interno della funzione. Osservare l'esecuzione del codice finché non si individua il problema.  
  
     Per ulteriori informazioni, vedere [esecuzione](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) di [istruzioni e debug di script e applicazioni Web](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Modifica delle configurazioni predefinite  
 Se si desidera, è possibile modificare le configurazioni di debug e di rilascio predefinite create da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per altre informazioni, vedere [procedura: impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>Per modificare la configurazione di debug predefinita  
  
1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul sito Web e scegliere **pagine delle proprietà** per aprire la finestra di dialogo **pagine delle proprietà** .  
  
2. Fare clic su **Opzioni di avvio**.  
  
3. Impostare **azione di avvio** sulla pagina Web che deve essere visualizzata per prima.  
  
4. In **debugger**verificare che sia selezionata l'opzione **debug ASP.NET** .  
  
     Per ulteriori informazioni, vedere [impostazioni delle pagine delle proprietà per i progetti web](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni e preparazione del debugger](../debugger/debugger-settings-and-preparation.md)   
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice gestito](../debugger/debugging-managed-code.md)
