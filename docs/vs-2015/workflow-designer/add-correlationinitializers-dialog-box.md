---
title: Aggiungi finestra di dialogo CorrelationInitializers | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0c90a2d0e0297a00454e38f428093a2f2db1e46d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001367"
---
# <a name="add-correlationinitializers-dialog-box"></a>Finestra di dialogo Aggiungi inizializzatori di correlazione
Il **Aggiungi inizializzatori di correlazione** finestra di dialogo viene utilizzata nella [!INCLUDE[wfd1](../includes/wfd1-md.md)] per configurare il **CorrelationInitializers** le proprietà del <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, e <xref:System.ServiceModel.Activities.ReceiveReply> attività. [!INCLUDE[crabout](../includes/crabout-md.md)] gli ActivityDesigner che utilizzano questa casella, vedere la [inviare](../workflow-designer/send-activity-designer.md), [ricezione](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), e [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) argomenti.  
  
 Gli inizializzatori di correlazione della raccolta specificata con questa finestra di dialogo possono inizializzare correlazioni tra le attività di messaggistica basate su query, di contesto, di contesto di callback o correlazioni richiesta-risposta.  
  
 La tabella seguente descrive gli elementi dell'interfaccia utente di **Aggiungi inizializzatori di correlazione** nella finestra di dialogo.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|----------------|-----------------|  
|**Aggiungi inizializzatore**|Scegliere il **initialize Aggiungi** casella per aggiungere un ulteriore inizializzatore alla raccolta.|  
|**Tipo di correlazione**|Consente di specificare il tipo di inizializzatore di correlazione. Sono disponibili quattro tipi:<br /><br /> 1.  Un inizializzatore di correlazione di callback che consente di specificare un oggetto <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2.  Un inizializzatore di correlazione di contesto che consente di specificare un oggetto <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3.  Un inizializzatore di correlazione richiesta-risposta che consente di specificare un oggetto <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4.  Un inizializzatore di correlazione query che consente di specificare un oggetto <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Per modificare il **CorrelationType**<br /><br /> 1.  Scheda per la riga specifica il **Aggiungi inizializzatore** DataGrid.<br />2.  Premere Ctrl + Tab per impostare lo stato attivo su **CorrelationTypeComboBox**<br />3.  Premere Alt + freccia giù per aprire la **ComboBox** e modificarlo.|  
|**Query XPath**|Una coppia chiave/valore che contiene le query usate per estrarre dati di correlazione dai messaggi in ingresso e in uscita. Questo elenco è valido solo in caso di utilizzo di tipi <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|  
  
## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Per avviare la finestra di dialogo Aggiungi inizializzatori di correlazione  
 Il **Aggiungi inizializzatori di correlazione** finestra di dialogo viene utilizzata per il **inviare**, **ricezione**, **ReceiveAndSendReply**, e  **SendAndReceiveReply** finestre di progettazione. Accesso è simile in ogni caso e il caso che comporta la **ricezione** progettazione questo esempio verrà usata per illustrare la procedura.  
  
 Il **Receive** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque vengono posizionate le attività in genere. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive. Selezionare il **Receive** ActivityDesigner e fare clic sul pulsante dei puntini di sospensione accanto al testo (raccolta) per il **CorrelationInitializers** proprietà nella griglia delle proprietà per il **Add Inizializzatori di correlazione** finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra di dialogo Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)