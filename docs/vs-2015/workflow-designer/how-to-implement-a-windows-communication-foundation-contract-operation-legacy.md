---
title: "Procedura: implementare un'operazione di contratto di Windows Communication Foundation (Legacy) | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f4277de8f97951847bf448636fec1b9c652f9359
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527456"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Procedura: implementare un'operazione del contratto di Windows Communication Foundation (legacy)
In questo argomento viene descritto come implementare un'operazione di contratto [!INCLUDE[indigo1](../includes/indigo1-md.md)] usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Dopo avere trascinato un **ReceiveActivity** attività dalla casella degli strumenti all'area di progettazione del flusso di lavoro, ovvero creerai un nuovo [!INCLUDE[indigo2](../includes/indigo2-md.md)] del contratto o importare un contratto esistente e implementare le operazioni. Si seleziona e/o creare il contratto e le relative operazioni tramite il [sceglie finestra di dialogo operazione (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### <a name="to-implement-a-wcf-contract-operation"></a>Per implementare un'operazione del contratto WCF  
  
1.  Fare doppio clic sui **ReceiveActivity** attività nella finestra di progettazione o fare clic sui puntini di sospensione accanto al **ServiceOperationInfo** proprietà nel **proprietà** riquadro.  
  
2.  Eseguire una delle operazioni seguenti:  
  
    -   Fare clic su **Aggiungi contratto** nell'angolo superiore destro della finestra di dialogo. Vengono creati un nuovo contratto e una nuova operazione [!INCLUDE[indigo2](../includes/indigo2-md.md)].  
  
         oppure  
  
    -   Fare clic su **importazione** nell'angolo superiore destro della finestra di dialogo. Il [individuare e selezionare una finestra di dialogo tipo .NET (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) apre. Cercare un assembly o un progetto contenente il contratto desiderato. Selezionare il contratto e fare clic su **OK**.  
  
     Dopo aver creato o importato un contratto, sarà possibile aggiungervi nuove operazioni. Per aggiungere una nuova operazione, selezionare il contratto e fare clic su **Aggiungi operazione** nell'angolo superiore destro della finestra di dialogo. Dopo aver inserito tutte le operazioni, andare al passaggio 3.  
  
3.  Selezionare l'operazione che si desidera associare il **ReceiveActivity** attività. È possibile modificare la definizione dell'operazione modificando il nome, i parametri, le proprietà e le impostazioni relative alle autorizzazioni.  
  
     Per modificare il nome, immettere il nuovo nome nella **nome dell'operazione** casella di testo.  
  
     Scegliere il **parametri** pressione di tab per accedere ai parametri dell'operazione. È possibile modificare il nome, il tipo o la direzione di un parametro così come aggiungere o eliminare parametri dall'operazione.  
  
     Scegliere il **proprietà** pressione di tab per accedere alla funzionalità di exchange supportate e a livello di messaggio di operazione protezione dell'operazione.  
  
     Scegliere il **autorizzazioni** tab per specificare quale gruppo è consentito per implementare l'operazione.  
  
4.  Fare clic su **OK** e il **ReceiveActivity** attività visualizzerà il nome dell'operazione per l'operazione che sta implementando.  
  
5.  Posizionare le attività del flusso di lavoro si intende usare per l'implementazione di tale operazione all'interno di **ReceiveActivity** attività.  
  
## <a name="see-also"></a>Vedere anche  
 [Dialogo Seleziona operazione (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Procedura: richiamare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)