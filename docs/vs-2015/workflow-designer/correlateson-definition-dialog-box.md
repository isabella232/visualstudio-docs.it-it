---
title: Finestra di dialogo definizione CorrelatesOn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2a9a6f7ec6b8bf246ebfc03c166780b229e1aee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656943"
---
# <a name="correlateson-definition-dialog-box"></a>Finestra di dialogo Definizione di CorrelatesOn
La finestra di dialogo **CorrelatesOn** viene utilizzata in [!INCLUDE[wfd1](../includes/wfd1-md.md)] per modificare la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> proprietà di un' <xref:System.ServiceModel.Activities.Receive> attività. [!INCLUDE[crdefault](../includes/crdefault-md.md)] argomento [Receive](../workflow-designer/receive-activity-designer.md) .

 La correlazione tra le attività <xref:System.ServiceModel.Activities.Receive> specifica come operazioni del servizio diverse si connettono tra loro in un flusso di lavoro.

 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente (UI) della finestra di dialogo **CorrelatesOn** .

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**CorrelatesWith**|Oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per indirizzare il messaggio all'istanza del flusso di lavoro appropriata.|
|**Query XPath**|Una coppia chiave/valore che contiene le query usate per estrarre dati di correlazione dai messaggi in ingresso. Questa proprietà corrisponde alla proprietà <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Le query XPath sono incluse in un oggetto <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Per aprire la finestra di dialogo CorrelatesOn.
 È possibile trascinare l'ActivityDesigner **Receive** dalla **casella degli strumenti** e rilasciarlo nell'area in cui [!INCLUDE[wfd2](../includes/wfd2-md.md)] vengono in genere posizionate le attività. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive. Selezionare l'ActivityDesigner **Receive** e fare clic sul pulsante con i puntini di sospensione accanto al testo (raccolta) per la proprietà **CorrelatesOn** nella griglia delle proprietà per visualizzare la finestra di dialogo **definizione CorrelatesOn** .

## <a name="see-also"></a>Vedere anche
 <xref:System.ServiceModel.Activities.Receive>Finestra di dialogo [Aggiungi CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) della finestra di dialogo [Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)