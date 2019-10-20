---
title: "Procedura: implementare un'operazione del contratto Windows Communication Foundation (legacy) | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f6f54e781dfae15b4b1c1159d73ac3495b35c21
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603871"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Procedura: implementare un'operazione del contratto di Windows Communication Foundation (legacy)
In questo argomento viene descritto come implementare un'operazione di contratto [!INCLUDE[indigo1](../includes/indigo1-md.md)] usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Dopo avere trascinato un'attività **ReceiveActivity** dalla casella degli strumenti all'area di progettazione del flusso di lavoro, sarà possibile creare un nuovo contratto di [!INCLUDE[indigo2](../includes/indigo2-md.md)] o importare un contratto esistente e implementare le operazioni. Selezionare e/o creare il contratto e le relative operazioni tramite la finestra di [dialogo Seleziona operazione (legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md).

### <a name="to-implement-a-wcf-contract-operation"></a>Per implementare un'operazione del contratto WCF

1. Fare doppio clic sull'attività **ReceiveActivity** nella finestra di progettazione o fare clic sui puntini di sospensione accanto alla proprietà **ServiceOperationInfo** nel riquadro **proprietà** .

2. Effettuare una delle operazioni riportate di seguito:

   - Fare clic su **Aggiungi contratto** nell'angolo superiore destro della finestra di dialogo. Vengono creati un nuovo contratto e una nuova operazione [!INCLUDE[indigo2](../includes/indigo2-md.md)].

      oppure

   - Fare clic su **Importa** nell'angolo superiore destro della finestra di dialogo. Verrà visualizzata la finestra di [dialogo Cerca e seleziona un tipo .NET (legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) . Cercare un assembly o un progetto contenente il contratto desiderato. Selezionare il contratto e fare clic su **OK**.

     Dopo aver creato o importato un contratto, sarà possibile aggiungervi nuove operazioni. Per aggiungere una nuova operazione, selezionare il contratto e fare clic su **Aggiungi operazione** nell'angolo superiore destro della finestra di dialogo. Dopo aver inserito tutte le operazioni, andare al passaggio 3.

3. Selezionare l'operazione che si desidera associare all'attività **ReceiveActivity** . È possibile modificare la definizione dell'operazione modificando il nome, i parametri, le proprietà e le impostazioni relative alle autorizzazioni.

    Per modificare il nome, immettere il nuovo nome nella casella di testo **nome operazione** .

    Fare clic sulla scheda **parametri** per accedere ai parametri dell'operazione. È possibile modificare il nome, il tipo o la direzione di un parametro così come aggiungere o eliminare parametri dall'operazione.

    Fare clic sulla scheda **Proprietà** per accedere al livello di protezione dell'operazione e alla funzionalità di scambio di messaggi supportata.

    Fare clic sulla scheda **autorizzazioni** per specificare i gruppi a cui è consentito implementare l'operazione.

4. Fare clic su **OK** e l'attività **ReceiveActivity** visualizzerà il nome dell'operazione per l'operazione che sta implementando.

5. Inserire le attività del flusso di lavoro che si intende utilizzare per l'implementazione dell'operazione all'interno dell'attività **ReceiveActivity** .

## <a name="see-also"></a>Vedere anche
 Finestra di [dialogo Seleziona operazione (legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md) [procedura: richiamare un'operazione del contratto WCF (legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)