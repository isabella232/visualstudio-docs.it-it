---
title: Progettazione flussi di lavoro-finestra di dialogo Aggiungi CorrelationInitializers
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d2a0b0f7c76b392d5d2d0135c3ab6e370f8678e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114292"
---
# <a name="add-correlationinitializers-dialog-box"></a>Finestra di dialogo Aggiungi inizializzatori di correlazione

La finestra di dialogo **Aggiungi inizializzatori di correlazione** viene utilizzata in Progettazione flussi di lavoro per configurare le proprietà **CorrelationInitializers** delle <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> attività,, <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply> . Per ulteriori informazioni sull'ActivityDesigner che utilizza questa casella, vedere gli argomenti [Send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)e [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

Gli inizializzatori di correlazione nella raccolta specificata con questa finestra di dialogo possono inizializzare le seguenti correlazioni tra le attività di messaggistica:

- basata su query
- contesto
- contesto di callback
- Request/Reply

Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente (UI) della finestra di dialogo **Aggiungi inizializzatori di correlazione** :

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**Aggiungi inizializzatore**|Fare clic sulla casella **Aggiungi inizializzazione** per aggiungere un inizializzatore aggiuntivo alla raccolta.|
|**Tipo correlazione**|Consente di specificare il tipo di inizializzatore di correlazione. Sono disponibili quattro tipi:<br /><br /> 1. inizializzatore di correlazione di callback per specificare un oggetto <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> .<br />2. inizializzatore di correlazione del contesto per specificare un oggetto <xref:System.ServiceModel.Activities.CorrelationInitializer> .<br />3. inizializzatore di correlazione Request/Reply per specificare un oggetto <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> .<br />4. inizializzatore di correlazione di query per specificare un oggetto <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> .<br /><br /> Per modificare il **CorrelationType**<br /><br /> 1. Tab per la riga specifica nel DataGrid **Aggiungi inizializzatore** .<br />2. per impostare lo stato attivo su **CorrelationTypeComboBox**, premere **CTRL** + **Tab**.<br />3. Premere ALT + freccia giù per visualizzare la **casella combinata** e modificarla.|
|**Query XPath**|Una coppia chiave/valore che contiene le query usate per estrarre dati di correlazione dai messaggi in ingresso e in uscita. Questo elenco è valido solo in caso di utilizzo di tipi <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Per avviare la finestra di dialogo Aggiungi inizializzatori di correlazione

 La finestra di dialogo **Aggiungi inizializzatori di correlazione** viene utilizzata dalle finestre di progettazione **Send**, **Receive**, **ReceiveAndSendReply**e **SendAndReceiveReply** . L'accesso è simile in ogni caso e viene usato il caso che include la finestra di progettazione di **ricezione** per illustrare la procedura.

 È possibile trascinare l'ActivityDesigner **Receive** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro ogni volta che vengono inserite le attività. Se si elimina l'ActivityDesigner **Receive** , viene creata un' <xref:System.ServiceModel.Activities.Receive> attività con il valore predefinito <xref:System.Activities.Activity.DisplayName%2A> Receive. Selezionare l'ActivityDesigner **Receive** e fare clic sul pulsante con i puntini di sospensione accanto al testo (raccolta) per la proprietà **CorrelationInitializers** nella griglia delle proprietà per visualizzare la finestra di dialogo **Aggiungi inizializzatori di correlazione** .

## <a name="see-also"></a>Vedere anche

- [Finestra di dialogo Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)
