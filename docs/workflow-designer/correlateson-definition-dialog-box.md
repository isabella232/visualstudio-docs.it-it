---
title: Finestra di progettazione del flusso di lavoro - finestra di dialogo Definizione di CorrelatesOn
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3cfd9d43a8152b629635103b399ef0d7566e4867
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933118"
---
# <a name="correlateson-definition-dialog-box"></a>Finestra di dialogo Definizione di CorrelatesOn

Il **CorrelatesOn** finestra di dialogo viene utilizzata nella finestra di progettazione del flusso di lavoro per modificare le <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> proprietà di un <xref:System.ServiceModel.Activities.Receive> attività. Per altre informazioni, vedere [ricezione ActivityDesigner](../workflow-designer/receive-activity-designer.md).

La correlazione tra le attività <xref:System.ServiceModel.Activities.Receive> specifica come operazioni del servizio diverse si connettono tra loro in un flusso di lavoro.

La tabella seguente descrive gli elementi dell'interfaccia utente di **CorrelatesOn** nella finestra di dialogo.

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**CorrelatesWith**|Oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per indirizzare il messaggio all'istanza del flusso di lavoro appropriata.|
|**Query XPath**|Una coppia chiave/valore che contiene le query usate per estrarre dati di correlazione dai messaggi in ingresso. Questo valore corrisponde al <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> proprietà. Le query XPath sono incluse in un oggetto <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Per aprire la finestra di dialogo CorrelatesOn.

Il **Receive** ActivityDesigner può essere trascinato dalla **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro, ogni volta che vengono in genere posizionate le attività. La finestra di progettazione di attività di rilascio crea un <xref:System.ServiceModel.Activities.Receive> attività predefinito <xref:System.Activities.Activity.DisplayName%2A> di ricezione. Per aprire la **definizione di CorrelatesOn** finestra di dialogo, seleziona la **ricezione** attività della finestra di progettazione e quindi nella griglia delle proprietà, selezionare il pulsante con puntini di sospensione accanto al testo di raccolta per il  **CorrelatesOn** proprietà.

## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Activities.Receive>
- [Finestra di dialogo Aggiungi inizializzatori di correlazione](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Aggiungi finestra di dialogo di correlazione](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Finestra di dialogo Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)