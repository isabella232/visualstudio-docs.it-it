---
title: "Procedura: Richiamare un'operazione di contratto di Windows Communication Foundation (Legacy) | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d42c9698c6d3a247601909909c49fa92d2d29978
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056666"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Procedura: Richiamare un'operazione del contratto Windows Communication Foundation (legacy)
In questo argomento viene descritto come richiamare un'operazione di contratto [!INCLUDE[indigo1](../includes/indigo1-md.md)] usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Dopo avere trascinato un **SendActivity** attività dalla casella degli strumenti all'area di progettazione del flusso di lavoro, è necessario importare un contratto esistente e determinare quale operazione verrà richiamata da quella **SendActivity** attività. Si seleziona il contratto e le relative operazioni tramite il [sceglie finestra di dialogo operazione (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Se con il servizio si sta usando un file di configurazione, sarà inoltre necessario specificare un elemento <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> identifica la configurazione dell'endpoint che l'attività di trasmissione utilizzerà per connettersi al servizio del flusso di lavoro.  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Per richiamare un'operazione di contratto WCF da un'attività SendActivity  
  
1. Fare doppio clic sui **SendActivity** attività nella finestra di progettazione o fare clic sui puntini di sospensione accanto al **ServiceOperationInfo** proprietà nel **proprietà** riquadro.  
  
2. Quando la **Seleziona operazione** verrà visualizzata la finestra di dialogo, fare clic su **importazione** nell'angolo superiore destro della finestra di dialogo.  
  
     Il [individuare e selezionare una finestra di dialogo tipo .NET (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) apre.  
  
3. Cercare un assembly o un progetto contenente il contratto desiderato.  
  
4. Selezionare il contratto e fare clic su **OK**.  
  
5. Sotto **operazioni disponibili**, selezionare l'operazione da richiamare e fare clic su **OK**.  
  
### <a name="to-specify-a-channel-token"></a>Per specificare un token del canale  
  
1. Selezionare l'attività <xref:System.Workflow.Activities.SendActivity> nella finestra di progettazione.  
  
2. Nel **delle proprietà** riquadro, specificare un nome per il <xref:System.Workflow.Activities.ChannelToken>. Questo nome identifica in modo univoco il token del canale.  
  
3. Espandere il nodo del token del canale e specificare un nome per l'endpoint client che si desidera usare nel campo <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>. La configurazione di endpoint con lo stesso nome nel file di configurazione verrà usata per configurare il canale.  
  
4. Creare la configurazione dell'endpoint nel file di configurazione, se non esiste già. Per altre informazioni sulla configurazione del client, vedere [WCF Client Overview](http://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).  
  
## <a name="see-also"></a>Vedere anche  
 [Dialogo Seleziona operazione (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Procedura: Implementare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)