---
title: Finestra di dialogo Aggiungi inizializzatori di correlazione
description: Informazioni su come usare la finestra di dialogo Aggiungi inizializzatori di correlazione in Progettazione flussi di lavoro per configurare le proprietà CorrelationInitializers delle attività Send, Receive e SendReply.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 4085d8536c9d8f15e8928e010bb2744551a7747c
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963211"
---
# <a name="add-correlationinitializers-dialog-box"></a>Finestra di dialogo Aggiungi inizializzatori di correlazione

La **finestra di dialogo Aggiungi** inizializzatori di correlazione viene usata Progettazione flussi di lavoro per configurare le proprietà **CorrelationInitializers** delle <xref:System.ServiceModel.Activities.Send> attività , , e <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.ReceiveReply> . Per altre informazioni sugli ActivityDesigner che usano questa casella, vedere gli argomenti [Send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)e [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

Gli inizializzatori di correlazione nella raccolta specificata con questa finestra di dialogo possono inizializzare le correlazioni seguenti tra le attività di messaggistica:

- basato su query
- contesto
- contesto di callback
- request-reply

Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente della finestra di dialogo Aggiungi **inizializzatori** di correlazione:

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**Aggiungi inizializzatore**|Fare clic **sulla casella Aggiungi** inizializzatore per aggiungere un inizializzatore aggiuntivo alla raccolta.|
|**Tipo correlazione**|Consente di specificare il tipo di inizializzatore di correlazione. Sono disponibili quattro tipi:<br /><br /> 1. Inizializzatore di correlazione di callback per specificare un oggetto <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> .<br />2. Inizializzatore di correlazione del contesto per specificare un oggetto <xref:System.ServiceModel.Activities.CorrelationInitializer> .<br />3. Inizializzatore di correlazione request/reply per specificare un oggetto <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> .<br />4. Inizializzatore di correlazione di query per specificare un oggetto <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> .<br /><br /> Per modificare **CorrelationType**<br /><br /> 1. Premere TAB per selezionare la riga specifica in Add Initializer DataGrid **(Aggiungi datagrid inizializzatore).**<br />2. Per impostare lo stato attivo **su CorrelationTypeComboBox,** premere  + **CTRL+TAB.**<br />3. Premere ALT+FRECCIA GIÙ per visualizzare il **controllo ComboBox** e modificarlo.|
|**Query XPath**|Una coppia chiave/valore che contiene le query usate per estrarre dati di correlazione dai messaggi in ingresso e in uscita. Questo elenco è valido solo in caso di utilizzo di tipi <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Per avviare la finestra di dialogo Aggiungi inizializzatori di correlazione

 La **finestra di dialogo Aggiungi** inizializzatori di correlazione viene usata dalle finestre di progettazione **Send**, **Receive**, **ReceiveAndSendReply** e **SendAndReceiveReply** . L'accesso è simile in ogni caso e  il caso che interessa la finestra di progettazione ricezione viene usato qui per illustrare la procedura.

 L'ActivityDesigner **Receive** può essere trascinato dalla **casella** degli strumenti e rilasciato nella Progettazione flussi di lavoro in cui sono posizionate le attività. L'eliminazione **dell'ActivityDesigner Receive** crea <xref:System.ServiceModel.Activities.Receive> un'attività con il <xref:System.Activities.Activity.DisplayName%2A> valore predefinito Receive. Selezionare l'ActivityDesigner **Receive** e fare clic sul pulsante con i puntini di sospensione accanto  al testo (Raccolta) per la proprietà **CorrelationInitializers** nella griglia delle proprietà per visualizzare la finestra di dialogo Aggiungi inizializzatori di correlazione.

## <a name="see-also"></a>Vedi anche

- [Finestra di dialogo Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)
