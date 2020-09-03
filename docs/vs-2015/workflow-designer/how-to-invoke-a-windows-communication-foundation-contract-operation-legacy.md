---
title: "Procedura: richiamare un'operazione del contratto Windows Communication Foundation (legacy) | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f42600a739561a27a6dd8f6caa237027bac4554
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603694"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Procedura: richiamare un'operazione del contratto Windows Communication Foundation (legacy)
In questo argomento viene descritto come richiamare un'operazione di contratto [!INCLUDE[indigo1](../includes/indigo1-md.md)] usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Dopo aver trascinato un'attività **SendActivity** dalla casella degli strumenti all'area di progettazione del flusso di lavoro, è necessario importare un contratto esistente e determinare quale operazione verrà richiamata dall'attività **SendActivity** . È possibile selezionare il contratto e le relative operazioni tramite la finestra di [dialogo Seleziona operazione (legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md).

 Se con il servizio si sta usando un file di configurazione, sarà inoltre necessario specificare un elemento <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> identifica la configurazione dell'endpoint che l'attività di trasmissione utilizzerà per connettersi al servizio del flusso di lavoro.

### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Per richiamare un'operazione di contratto WCF da un'attività SendActivity

1. Fare doppio clic sull'attività **SendActivity** nella finestra di progettazione o fare clic sui puntini di sospensione accanto alla proprietà **ServiceOperationInfo** nel riquadro **proprietà** .

2. Quando viene visualizzata la finestra di dialogo **Scegli operazione** , fare clic su **Importa** nell'angolo superiore destro della finestra di dialogo.

     Verrà visualizzata la finestra di [dialogo Cerca e seleziona un tipo .NET (legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) .

3. Cercare un assembly o un progetto contenente il contratto desiderato.

4. Selezionare il contratto e fare clic su **OK**.

5. In **operazioni disponibili**selezionare l'operazione che si desidera richiamare, quindi fare clic su **OK**.

### <a name="to-specify-a-channel-token"></a>Per specificare un token del canale

1. Selezionare l'attività <xref:System.Workflow.Activities.SendActivity> nella finestra di progettazione.

2. Nel riquadro **Proprietà** specificare un nome per il <xref:System.Workflow.Activities.ChannelToken> . Questo nome identifica in modo univoco il token del canale.

3. Espandere il nodo del token del canale e specificare un nome per l'endpoint client che si desidera usare nel campo <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>. La configurazione di endpoint con lo stesso nome nel file di configurazione verrà usata per configurare il canale.

4. Creare la configurazione dell'endpoint nel file di configurazione, se non esiste già. Per ulteriori informazioni sulla configurazione del client, vedere [Cenni preliminari sui client WCF](https://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).

## <a name="see-also"></a>Vedere anche
 Finestra di [dialogo Seleziona operazione (legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md) [procedura: implementare un'operazione del contratto WCF (legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)