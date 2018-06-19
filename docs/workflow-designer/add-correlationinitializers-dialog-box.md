---
title: Finestra di progettazione del flusso di lavoro - finestra di dialogo di CorrelationInitializers Aggiungi
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc122840607b62a966e5224662ec2d557e5c8ed5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975146"
---
# <a name="add-correlationinitializers-dialog-box"></a>Finestra di dialogo Aggiungi inizializzatori di correlazione

Il **Aggiungi inizializzatori di correlazione** la finestra di dialogo viene utilizzata in Progettazione flussi di lavoro di Windows per configurare il **CorrelationInitializers** le proprietà del <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, e <xref:System.ServiceModel.Activities.ReceiveReply> le attività. Per ulteriori informazioni sulle finestre di progettazione di attività che utilizzano questa casella, vedere il [inviare](../workflow-designer/send-activity-designer.md), [ricezione](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), e [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) argomenti.

Gli inizializzatori di correlazione della raccolta specificata con questa finestra di dialogo è possono inizializzare le correlazioni tra le attività di messaggistica seguenti:

- basate su query
- contesto
- contesto di callback
- request/reply

Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente di **Aggiungi inizializzatori di correlazione** finestra di dialogo:

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Aggiungi inizializzatore**|Fare clic su di **Aggiungi initialize** casella per aggiungere un ulteriore inizializzatore alla raccolta.|
|**Tipo di correlazione**|Consente di specificare il tipo di inizializzatore di correlazione. Sono disponibili quattro tipi:<br /><br /> 1. Un inizializzatore di correlazione di callback che consente di specificare un oggetto <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2. Un inizializzatore di correlazione di contesto che consente di specificare un oggetto <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3. Un inizializzatore di correlazione richiesta-risposta che consente di specificare un oggetto <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4. Un inizializzatore di correlazione query che consente di specificare un oggetto <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Per modificare il **CorrelationType**<br /><br /> 1. Scheda alla riga specifica nel **Aggiungi inizializzatore** DataGrid.<br />2. Per impostare lo stato attivo **CorrelationTypeComboBox**, premere **Ctrl**+**scheda**.<br />3. Premere Alt + freccia giù per aprire la **ComboBox** e modificarlo.|
|**Query XPath**|Una coppia chiave/valore che contiene le query usate per estrarre dati di correlazione dai messaggi in ingresso e in uscita. Questo elenco è valido solo in caso di utilizzo di tipi <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Per avviare la finestra di dialogo Aggiungi inizializzatori di correlazione

 Il **Aggiungi inizializzatori di correlazione** la finestra di dialogo viene utilizzata la **inviare**, **ricezione**, **ReceiveAndSendReply**, e  **SendAndReceiveReply** finestre di progettazione. Accesso è simile in ogni caso e quello che prevede il **ricezione** designer viene usato per illustrare la procedura.

 Il **Receive** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che vengono posizionate le attività. Eliminazione di **Receive** ActivityDesigner crea un <xref:System.ServiceModel.Activities.Receive> attività con un valore predefinito <xref:System.Activities.Activity.DisplayName%2A> Receive. Selezionare il **ricezione** ActivityDesigner e fare clic sul pulsante con i puntini di sospensione accanto al testo (raccolta) per il **CorrelationInitializers** proprietà nella griglia delle proprietà per il **Aggiungi Inizializzatori di correlazione** finestra di dialogo.

## <a name="see-also"></a>Vedere anche

- [Aggiungere la finestra di dialogo di correlazione](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Finestra di dialogo Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)