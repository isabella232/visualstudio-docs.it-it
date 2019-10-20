---
title: 'Procedura: eseguire il debug di flussi di lavoro basati su ASP.NET (legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3bed38f5229cb489f663878759517480b48302c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668663"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Procedura: eseguire il debug di flussi di lavoro basati su ASP.NET (legacy)
In questo argomento viene descritto come eseguire il debug di applicazioni [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] basate su [!INCLUDE[wf](../includes/wf-md.md)] che fanno riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] in [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy.

 È possibile eseguire il debug di flussi di lavoro legacy avviati in ASP.NET o flussi di lavoro legacy pubblicati come servizio Web connettendoli al processo nel quale è ospitato il flusso di lavoro.

### <a name="to-debug-an-aspnet-based-workflow"></a>Per eseguire il debug del flusso di lavoro basato su ASP.NET

1. Abilitare il debug per l'applicazione ASP.NET impostando **debug = true** nel file Web. config.

2. Impostare la libreria del flusso di lavoro come progetto di avvio e impostare i punti di interruzione sul flusso di lavoro.

3. Immettere l'URL della pagina Web predefinita nella casella di testo opzioni di **debug** delle proprietà del progetto del flusso di lavoro **Avvia browser con URL esterno** .

4. Scegliere **Connetti a processo** dal menu **debug** .

5. Selezionare il processo a cui connettersi dall'elenco **processi disponibili** .

     Allegare al processo w3wp.exe, webdev.webserver o aspnet_wp che ospita il flusso di lavoro.

6. Fare clic su **Seleziona** accanto alla casella di testo **Connetti a** .

     Verrà visualizzata la finestra di dialogo **Seleziona tipo di codice** .

7. Selezionare **Esegui il debug di questi tipi di codice** e selezionare **flusso di lavoro**.

8. Fare clic su **OK**.

9. Scegliere **Connetti**.

10. Aprire la pagina Web predefinita in un browser e avviare il flusso di lavoro.

## <a name="see-also"></a>Vedere anche
 [Richiamo del debugger di Visual Studio per Windows Workflow Foundation (legacy)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [procedura: impostare punti di interruzione nei flussi di](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [lavoro legacy del debug](../workflow-designer/debugging-legacy-workflows.md) dei flussi di lavoro