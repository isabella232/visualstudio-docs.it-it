---
title: 'Procedura: eseguire il Debug di flussi di lavoro basati su ASP.NET (Legacy) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: d30cb54ea035dfac63cf3ab4761c2c7cb5376314
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529439"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Procedura: eseguire il debug di flussi di lavoro basati su ASP.NET (legacy)
In questo argomento viene descritto come eseguire il debug di applicazioni [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] basate su [!INCLUDE[wf](../includes/wf-md.md)] che fanno riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] in [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy.  
  
 È possibile eseguire il debug di flussi di lavoro legacy avviati in ASP.NET o flussi di lavoro legacy pubblicati come servizio Web connettendoli al processo nel quale è ospitato il flusso di lavoro.  
  
### <a name="to-debug-an-aspnet-based-workflow"></a>Per eseguire il debug del flusso di lavoro basato su ASP.NET  
  
1.  Abilitare il debug per l'applicazione ASP.NET impostando **debug = true** nel file Web. config.  
  
2.  Impostare la libreria del flusso di lavoro come progetto di avvio e impostare i punti di interruzione sul flusso di lavoro.  
  
3.  Immettere l'URL della pagina Web predefinita nelle proprietà del progetto flusso di lavoro **Debug** opzione **avvia il browser con URL esterno** casella di testo.  
  
4.  Selezionare **Connetti a processo** nel **Debug** menu.  
  
5.  Selezionare il processo da associare il **processi disponibili** elenco.  
  
     Allegare al processo w3wp.exe, webdev.webserver o aspnet_wp che ospita il flusso di lavoro.  
  
6.  Fare clic su **selezionate** accanto al **Allega a** casella di testo.  
  
     Il **Seleziona tipo di codice** verrà visualizzata la finestra di dialogo.  
  
7.  Selezionare **eseguire il Debug di questi tipi di codice** e selezionare **flusso di lavoro**.  
  
8.  Fare clic su **OK**.  
  
9. Scegliere **Connetti**.  
  
10. Aprire la pagina Web predefinita in un browser e avviare il flusso di lavoro.  
  
## <a name="see-also"></a>Vedere anche  
 [Richiamo del Debugger di Visual Studio per Windows Workflow Foundation (Legacy)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Procedura: impostare punti di interruzione nei flussi di lavoro (Legacy)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)