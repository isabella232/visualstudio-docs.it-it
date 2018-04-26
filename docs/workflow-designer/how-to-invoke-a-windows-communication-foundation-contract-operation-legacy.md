---
title: "Finestra di progettazione del flusso di lavoro - procedura: richiamare un'operazione di contratto di Windows Communication Foundation (Legacy)"
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b39d2132b29ec1f8fbfd8339bdb8f81e6f752a0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Procedura: richiamare un'operazione del contratto Windows Communication Foundation (legacy)

In questo argomento viene descritto come richiamare un'operazione del contratto Windows Communication Foundation (WCF) mediante Progettazione flussi di lavoro Windows legacy che fa riferimento a .NET Framework versione 3.5 o la WinFX.

Dopo avere trascinato un **SendActivity** attività dalla casella degli strumenti all'area di progettazione del flusso di lavoro, importare un contratto esistente. Determinare quale operazione viene richiamata dal **SendActivity** attività. Selezionare il contratto e le operazioni tramite il [scegliere finestra di dialogo operazione (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md).

Inoltre, se si utilizza un file di configurazione con il servizio, è necessario specificare un <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> identifica la configurazione dell'endpoint che l'attività di trasmissione utilizzerà per connettersi al servizio del flusso di lavoro.

## <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Per richiamare un'operazione di contratto WCF da un'attività SendActivity

1.  Fare doppio clic su di **SendActivity** attività nella finestra di progettazione o fare clic sui puntini di sospensione accanto al **ServiceOperationInfo** proprietà il **proprietà** riquadro.

2.  Quando il **Seleziona operazione** si apre la finestra di dialogo, fare clic su **importazione** nell'angolo superiore destro della finestra di dialogo.

     Il [Cerca e seleziona una casella di dialogo tipo .NET (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) apre.

3.  Cercare un assembly o un progetto contenente il contratto desiderato.

4.  Selezionare il contratto e fare clic su **OK**.

5.  In **operazioni disponibili**, selezionare l'operazione che si desidera richiamare e fare clic su **OK**.

## <a name="to-specify-a-channel-token"></a>Per specificare un token del canale

1.  Selezionare l'attività <xref:System.Workflow.Activities.SendActivity> nella finestra di progettazione.

2.  Nel **proprietà** riquadro, specificare un nome per il <xref:System.Workflow.Activities.ChannelToken>. Questo nome identifica in modo univoco il token del canale.

3.  Espandere il nodo del token del canale e specificare un nome per l'endpoint client che si desidera usare nel campo <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>. La configurazione dell'endpoint con lo stesso nome nel file di configurazione viene utilizzata per configurare il canale.

4.  Creare la configurazione dell'endpoint nel file di configurazione, se non esiste già. Per ulteriori informazioni sulla configurazione del client, vedere [panoramica dei Client WCF](/dotnet/framework/wcf/wcf-client-overview).

## <a name="see-also"></a>Vedere anche

- [Finestra di dialogo Seleziona operazione (legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [Procedura: implementare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)