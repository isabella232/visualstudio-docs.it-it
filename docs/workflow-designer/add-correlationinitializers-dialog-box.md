---
title: Finestra di progettazione del flusso di lavoro - Aggiungi finestra di dialogo di inizializzatori di correlazione
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cdd41044117e0cbbb132dca637012571e0864e73
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043401"
---
# <a name="add-correlationinitializers-dialog-box"></a>Finestra di dialogo Aggiungi inizializzatori di correlazione

Il **Aggiungi inizializzatori di correlazione** finestra di dialogo viene utilizzata nella finestra di progettazione del flusso di lavoro per configurare il **CorrelationInitializers** le proprietà del <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, e <xref:System.ServiceModel.Activities.ReceiveReply> attività. Per altre informazioni sull'ActivityDesigner che utilizzano questa casella, vedere la [inviare](../workflow-designer/send-activity-designer.md), [ricezione](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), e [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) argomenti.

Gli inizializzatori di correlazione della raccolta specificata con questa finestra di dialogo possono inizializzare le correlazioni tra le attività di messaggistica seguenti:

- basato su query
- contesto
- contesto di callback
- request-reply

La tabella seguente descrive gli elementi dell'interfaccia utente di **Aggiungi inizializzatori di correlazione** nella finestra di dialogo:

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**Aggiungi inizializzatore**|Scegliere il **initialize Aggiungi** casella per aggiungere un ulteriore inizializzatore alla raccolta.|
|**Tipo di correlazione**|Consente di specificare il tipo di inizializzatore di correlazione. Sono disponibili quattro tipi:<br /><br /> 1. Un inizializzatore di correlazione di callback che consente di specificare un oggetto <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2. Un inizializzatore di correlazione di contesto che consente di specificare un oggetto <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3. Un inizializzatore di correlazione richiesta-risposta che consente di specificare un oggetto <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4. Un inizializzatore di correlazione query che consente di specificare un oggetto <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Per modificare il **CorrelationType**<br /><br /> 1. Scheda per la riga specifica il **Aggiungi inizializzatore** DataGrid.<br />2. Per impostare lo stato attivo **CorrelationTypeComboBox**, premere **Ctrl**+**scheda**.<br />3. Premere Alt + freccia giù per aprire la **ComboBox** e modificarlo.|
|**Query XPath**|Una coppia chiave/valore che contiene le query usate per estrarre dati di correlazione dai messaggi in ingresso e in uscita. Questo elenco è valido solo in caso di utilizzo di tipi <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Per avviare la finestra di dialogo Aggiungi inizializzatori di correlazione

 Il **Aggiungi inizializzatori di correlazione** finestra di dialogo viene utilizzata per il **inviare**, **ricezione**, **ReceiveAndSendReply**, e  **SendAndReceiveReply** finestre di progettazione. Accesso è simile in ogni caso e il caso che comporta la **ricezione** designer viene usato per illustrare la procedura.

 Il **Receive** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che vengono posizionate le attività. Eliminare il **Receive** consente di creare un <xref:System.ServiceModel.Activities.Receive> attività con un valore predefinito <xref:System.Activities.Activity.DisplayName%2A> di ricezione. Selezionare il **Receive** ActivityDesigner e fare clic sul pulsante dei puntini di sospensione accanto al testo (raccolta) per il **CorrelationInitializers** proprietà nella griglia delle proprietà per il **Add Inizializzatori di correlazione** finestra di dialogo.

## <a name="see-also"></a>Vedere anche

- [Aggiungi finestra di dialogo di correlazione](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Finestra di dialogo Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)