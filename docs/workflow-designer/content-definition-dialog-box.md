---
title: Progettazione flussi di lavoro finestra di dialogo Definizione contenuto
description: Informazioni su come usare la finestra di dialogo Definizione contenuto per configurare le proprietà Content delle attività Send, Receive, SendReply e ReceiveReply.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: b3432853ce9e6aaf4f37c4a0c363099f4a61d988
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633700"
---
# <a name="content-definition-dialog-box"></a>Finestra di dialogo Definizione contenuto

La **finestra di** dialogo Definizione contenuto viene usata Progettazione flussi di lavoro per configurare le proprietà **Content** delle attività , , <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.ReceiveReply> . Per altre informazioni sugli ActivityDesigner che usano questa casella, vedere gli argomenti [Send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)e [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente della finestra **di dialogo Inizializza** correlazione:

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**Messaggio**|Specifica il contenuto del messaggio con la casella di  **testo Espressione** dati messaggio e il tipo usando l'elenco a discesa Tipo di messaggio . Per impostazione predefinita, la **definizione del contenuto utilizza** , che prevede un o un tipo di contratto di messaggio all'interno della definizione del servizio del flusso di <xref:System.ServiceModel.Activities.ReceiveMessageContent> <xref:System.ServiceModel.Channels.Message> lavoro.|
|**Parametri**|Fare clic **sul pulsante** di opzione Parametri per usare , che prevede un <xref:System.ServiceModel.Activities.ReceiveParametersContent> contratto dati. Usare la griglia dei dati per impostare una raccolta generica di coppie chiave/valore <xref:System.Activities.OutArgument> i cui valori vengono assegnati ai parametri variabili nel flusso di lavoro corrente.|

La **finestra di** dialogo Definizione contenuto viene usata dalle finestre di progettazione **Send**, **Receive**, **ReceiveAndSendReply** e **SendAndReceiveReply** . La procedura di accesso è simile per tutte le finestre. In questo esempio verrà usata la finestra di progettazione Receive.

L'ActivityDesigner **Receive** può essere  trascinato dalla casella degli strumenti e rilasciato nella Progettazione flussi di lavoro in cui vengono in genere inserite le attività. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive. Selezionare **l'ActivityDesigner** Receive e fare clic sul pulsante con i puntini di sospensione  accanto al testo (Contenuto) per la proprietà **Content** nella griglia delle proprietà per visualizzare la finestra di dialogo Definizione contenuto.

Il contenuto può essere specificato all'interno **della sezione Message** per un'attività o <xref:System.ServiceModel.Activities.ReceiveMessageContent> all'interno **della sezione Parameter** per un'attività. <xref:System.ServiceModel.Activities.ReceiveParametersContent>

## <a name="see-also"></a>Vedi anche

- [Guida dell'interfaccia utente della finestra di progettazione dei flussi di lavoro](browse-and-select-a-dotnet-type-dialog-box.md)