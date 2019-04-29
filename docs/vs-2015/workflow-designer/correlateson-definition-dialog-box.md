---
title: Finestra di dialogo Definizione di CorrelatesOn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fd03e1a8615e75d3f00f79eb10b7a7ff97f0eb33
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977378"
---
# <a name="correlateson-definition-dialog-box"></a>Finestra di dialogo Definizione di CorrelatesOn
Il **CorrelatesOn** finestra di dialogo viene utilizzata nella [!INCLUDE[wfd1](../includes/wfd1-md.md)] per modificare la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> proprietà di un <xref:System.ServiceModel.Activities.Receive> attività. [!INCLUDE[crdefault](../includes/crdefault-md.md)] il [ricezione](../workflow-designer/receive-activity-designer.md) argomento.  
  
 La correlazione tra le attività <xref:System.ServiceModel.Activities.Receive> specifica come operazioni del servizio diverse si connettono tra loro in un flusso di lavoro.  
  
 La tabella seguente descrive gli elementi dell'interfaccia utente di **CorrelatesOn** nella finestra di dialogo.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|----------------|-----------------|  
|**CorrelatesWith**|Oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per indirizzare il messaggio all'istanza del flusso di lavoro appropriata.|  
|**Query XPath**|Una coppia chiave/valore che contiene le query usate per estrarre dati di correlazione dai messaggi in ingresso. Questa proprietà corrisponde alla proprietà <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Le query XPath sono incluse in un oggetto <xref:System.ServiceModel.MessageQuerySet>.|  
  
## <a name="to-launch-the-correlateson-dialog-box"></a>Per aprire la finestra di dialogo CorrelatesOn.  
 Il **Receive** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque vengono posizionate le attività in genere. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive. Selezionare il **Receive** ActivityDesigner e fare clic sul pulsante dei puntini di sospensione accanto al testo (raccolta) per il **CorrelatesOn** proprietà nella griglia delle proprietà per il **definizione di CorrelatesOn**  finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.ServiceModel.Activities.Receive>   
 [Aggiungi finestra di dialogo di inizializzatori di correlazione](../workflow-designer/add-correlationinitializers-dialog-box.md)   
 [Finestra di dialogo Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)