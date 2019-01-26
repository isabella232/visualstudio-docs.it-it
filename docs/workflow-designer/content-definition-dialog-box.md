---
title: Finestra di progettazione del flusso di lavoro - finestra di dialogo Definizione contenuto
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49d789e3cbf1a005462e4b23db698bc81c65164a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999938"
---
# <a name="content-definition-dialog-box"></a>Finestra di dialogo Definizione contenuto

Il **definizione del contenuto** finestra di dialogo viene utilizzata nella finestra di progettazione del flusso di lavoro per configurare il **contenuto** le proprietà del <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, e <xref:System.ServiceModel.Activities.ReceiveReply> attività. Per altre informazioni sull'ActivityDesigner che utilizzano questa casella, vedere la [inviare](../workflow-designer/send-activity-designer.md), [ricezione](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), e [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) argomenti.

La tabella seguente descrive gli elementi dell'interfaccia utente di **Inizializza correlazione** nella finestra di dialogo:

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**Messaggio**|Specifica il contenuto del messaggio con il **i dati del messaggio** casella di testo espressione e il tipo utilizzando il **tipo di messaggio** casella di riepilogo a discesa. Per impostazione predefinita, il **definizione del contenuto** Usa le <xref:System.ServiceModel.Activities.ReceiveMessageContent>, che prevede un <xref:System.ServiceModel.Channels.Message> o un tipo all'interno della definizione di servizio del flusso di lavoro di contratto di messaggio.|
|**Parametri**|Scegliere il **parametri** pulsante di opzione per usare <xref:System.ServiceModel.Activities.ReceiveParametersContent>, che prevede un contratto dati. Usare la griglia dei dati per impostare una raccolta generica di coppie chiave/valore <xref:System.Activities.OutArgument> i cui valori vengono assegnati ai parametri variabili nel flusso di lavoro corrente.|

Il **definizione del contenuto** finestra di dialogo viene utilizzata per il **inviare**, **ricezione**, **ReceiveAndSendReply**, e  **SendAndReceiveReply** finestre di progettazione. La procedura di accesso è simile per tutte le finestre. In questo esempio verrà usata la finestra di progettazione Receive.

Il **Receive** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che vengono in genere posizionate le attività. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive. Selezionare il **Receive** ActivityDesigner e fare clic sul pulsante dei puntini di sospensione accanto al testo (contenuto) per il **contenuto** proprietà nella griglia delle proprietà per il **definizione contenuto**finestra di dialogo.

Il contenuto può essere specificato all'interno di **messaggio** sezione per un <xref:System.ServiceModel.Activities.ReceiveMessageContent> attività o all'interno la **parametro** sezione per un <xref:System.ServiceModel.Activities.ReceiveParametersContent> attività.

## <a name="see-also"></a>Vedere anche

- [Guida dell'interfaccia utente della finestra di progettazione dei flussi di lavoro](../workflow-designer/workflow-designer-ui-help.md)