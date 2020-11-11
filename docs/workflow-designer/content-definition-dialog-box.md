---
title: Finestra di dialogo Progettazione flussi di lavoro-definizione del contenuto
description: Informazioni su come utilizzare la finestra di dialogo Definizione contenuto per configurare le proprietà di contenuto delle attività Send, Receive, SendReply e ReceiveReply.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2858c179d05645b3e47e6be27e386168392fcb48
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438165"
---
# <a name="content-definition-dialog-box"></a>Finestra di dialogo Definizione contenuto

La finestra di dialogo **Definizione contenuto** viene utilizzata in Progettazione flussi di lavoro per configurare le proprietà di **contenuto** delle <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> attività,, <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply> . Per ulteriori informazioni sull'ActivityDesigner che utilizza questa casella, vedere gli argomenti [Send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)e [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente (UI) della finestra di dialogo **Inizializza correlazione** :

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**Message**|Specifica il contenuto del messaggio con la casella di testo espressione **dati del messaggio** e il tipo utilizzando l'elenco a discesa **tipo di messaggio** . Per impostazione predefinita, la **definizione del contenuto** USA <xref:System.ServiceModel.Activities.ReceiveMessageContent> , che prevede un <xref:System.ServiceModel.Channels.Message> tipo o un tipo di contratto di messaggio all'interno della definizione del servizio flusso di lavoro.|
|**Parametri**|Fare clic sul pulsante di opzione **parametri** per usare <xref:System.ServiceModel.Activities.ReceiveParametersContent> , che prevede un contratto dati. Usare la griglia dei dati per impostare una raccolta generica di coppie chiave/valore <xref:System.Activities.OutArgument> i cui valori vengono assegnati ai parametri variabili nel flusso di lavoro corrente.|

La finestra di dialogo **Definizione contenuto** viene utilizzata dalle finestre di progettazione **Send** , **Receive** , **ReceiveAndSendReply** e **SendAndReceiveReply** . La procedura di accesso è simile per tutte le finestre. In questo esempio verrà usata la finestra di progettazione Receive.

È possibile trascinare l'ActivityDesigner **Receive** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando le attività vengono in genere posizionate. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive. Selezionare l'ActivityDesigner **Receive** e fare clic sul pulsante con i puntini di sospensione accanto al testo (contenuto) per la proprietà **Content** nella griglia delle proprietà per visualizzare la finestra di dialogo **Definizione contenuto** .

Il contenuto può essere specificato all'interno della sezione del **messaggio** relativa a un' <xref:System.ServiceModel.Activities.ReceiveMessageContent> attività o all'interno della sezione di **parametro** per un' <xref:System.ServiceModel.Activities.ReceiveParametersContent> attività.

## <a name="see-also"></a>Vedere anche

- [Guida dell'interfaccia utente della finestra di progettazione dei flussi di lavoro](browse-and-select-a-dotnet-type-dialog-box.md)