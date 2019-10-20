---
title: Finestra di dialogo Aggiungi CorrelationInitializers | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1402b90dfc78068546b510ce6b85379b1695f47
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672035"
---
# <a name="add-correlationinitializers-dialog-box"></a>Finestra di dialogo Aggiungi inizializzatori di correlazione
La finestra di dialogo **Aggiungi inizializzatori di correlazione** viene utilizzata in [!INCLUDE[wfd1](../includes/wfd1-md.md)] per configurare le proprietà **CorrelationInitializers** delle attività <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply>. [!INCLUDE[crabout](../includes/crabout-md.md)] gli ActivityDesigner che usano questa casella, vedere gli argomenti [Send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)e [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

 Gli inizializzatori di correlazione della raccolta specificata con questa finestra di dialogo possono inizializzare correlazioni tra le attività di messaggistica basate su query, di contesto, di contesto di callback o correlazioni richiesta-risposta.

 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente (UI) della finestra di dialogo **Aggiungi inizializzatori di correlazione** .

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Aggiungi inizializzatore**|Fare clic sulla casella **Aggiungi inizializzazione** per aggiungere un inizializzatore aggiuntivo alla raccolta.|
|**Tipo di correlazione**|Consente di specificare il tipo di inizializzatore di correlazione. Sono disponibili quattro tipi:<br /><br /> 1. inizializzatore di correlazione di callback per specificare un <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2. inizializzatore di correlazione del contesto per specificare un <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3. inizializzatore di correlazione Request/Reply per specificare un <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4. inizializzatore di correlazione di query per specificare un <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Per modificare il **CorrelationType**<br /><br /> 1. Tab per la riga specifica nel DataGrid **Aggiungi inizializzatore** .<br />2. Premere CTRL + TAB per impostare lo stato attivo su **CorrelationTypeComboBox**<br />3. Premere ALT + freccia giù per visualizzare la **casella combinata** e modificarla.|
|**Query XPath**|Una coppia chiave/valore che contiene le query usate per estrarre dati di correlazione dai messaggi in ingresso e in uscita. Questo elenco è valido solo in caso di utilizzo di tipi <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Per avviare la finestra di dialogo Aggiungi inizializzatori di correlazione
 La finestra di dialogo **Aggiungi inizializzatori di correlazione** viene utilizzata dalle finestre di progettazione **Send**, **Receive**, **ReceiveAndSendReply**e **SendAndReceiveReply** . L'accesso a tali elementi è simile in ogni caso e viene utilizzato in questo caso la finestra di progettazione di **ricezione** per illustrare la procedura.

 È possibile trascinare l'ActivityDesigner **Receive** dalla **casella degli strumenti** e rilasciarlo nell'area [!INCLUDE[wfd2](../includes/wfd2-md.md)] quando le attività vengono in genere posizionate. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive. Selezionare l'ActivityDesigner **Receive** e fare clic sul pulsante con i puntini di sospensione accanto al testo (raccolta) per la proprietà **CorrelationInitializers** nella griglia delle proprietà per visualizzare la finestra di dialogo **Aggiungi inizializzatori di correlazione** .

## <a name="see-also"></a>Vedere anche
 [Finestra di dialogo Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)