---
title: Finestra di progettazione del flusso di lavoro - finestra di dialogo Definizione contenuto
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f20a17cf7e01eafc75263bd2753d686908574752
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="content-definition-dialog-box"></a>Finestra di dialogo Definizione contenuto

Il **definizione contenuto** la finestra di dialogo viene utilizzata in Progettazione flussi di lavoro di Windows per configurare il **contenuto** le proprietà del <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, e <xref:System.ServiceModel.Activities.ReceiveReply> attività. Per ulteriori informazioni sulle finestre di progettazione di attività che utilizzano questa casella, vedere il [inviare](../workflow-designer/send-activity-designer.md), [ricezione](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), e [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) argomenti.

Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente di **Inizializza correlazione** finestra di dialogo:

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Messaggio**|Specifica il contenuto del messaggio con il **i dati del messaggio** casella di testo espressione e il tipo utilizzando il **tipo di messaggio** casella di riepilogo a discesa. Per impostazione predefinita, il **definizione contenuto** utilizza il <xref:System.ServiceModel.Activities.ReceiveMessageContent>, che prevede un <xref:System.ServiceModel.Channels.Message> o un tipo nella definizione del servizio del flusso di lavoro di contratto di messaggio.|
|**Parametri**|Fare clic su di **parametri** pulsante di opzione per utilizzare <xref:System.ServiceModel.Activities.ReceiveParametersContent>, che prevede un contratto dati. Usare la griglia dei dati per impostare una raccolta generica di coppie chiave/valore <xref:System.Activities.OutArgument> i cui valori vengono assegnati ai parametri variabili nel flusso di lavoro corrente.|

Il **definizione contenuto** la finestra di dialogo viene utilizzata la **inviare**, **ricezione**, **ReceiveAndSendReply**, e  **SendAndReceiveReply** finestre di progettazione. La procedura di accesso è simile per tutte le finestre. In questo esempio verrà usata la finestra di progettazione Receive.

Il **Receive** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che vengono in genere posizionate le attività. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive. Selezionare il **ricezione** ActivityDesigner e fare clic sul pulsante con i puntini di sospensione accanto al testo (contenuto) per il **contenuto** proprietà nella griglia delle proprietà per il **definizione contenuto**finestra di dialogo.

Il contenuto può essere specificato all'interno di **messaggio** sezione per un <xref:System.ServiceModel.Activities.ReceiveMessageContent> attività o all'interno di **parametro** sezione per un <xref:System.ServiceModel.Activities.ReceiveParametersContent> attività.

## <a name="see-also"></a>Vedere anche

- [Guida dell'interfaccia utente della finestra di progettazione dei flussi di lavoro](../workflow-designer/workflow-designer-ui-help.md)