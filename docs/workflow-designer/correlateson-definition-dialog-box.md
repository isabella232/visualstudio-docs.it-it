---
title: Finestra di dialogo definizione Progettazione flussi di lavoro-CorrelatesOn
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d2db5bbfa4f34d86d3bf20cfe6bcc42b3dc00d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876125"
---
# <a name="correlateson-definition-dialog-box"></a>Finestra di dialogo Definizione di CorrelatesOn

La finestra di dialogo **CorrelatesOn** viene utilizzata in Progettazione flussi di lavoro per modificare la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> proprietà di un' <xref:System.ServiceModel.Activities.Receive> attività. Per altre informazioni, vedere ActivityDesigner [Receive](../workflow-designer/receive-activity-designer.md).

La correlazione tra le attività <xref:System.ServiceModel.Activities.Receive> specifica come operazioni del servizio diverse si connettono tra loro in un flusso di lavoro.

Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente (UI) della finestra di dialogo **CorrelatesOn** .

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**CorrelatesWith**|Oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per indirizzare il messaggio all'istanza del flusso di lavoro appropriata.|
|**Query XPath**|Una coppia chiave/valore che contiene le query usate per estrarre dati di correlazione dai messaggi in ingresso. Questo valore corrisponde alla <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> Proprietà. Le query XPath sono incluse in un oggetto <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Per aprire la finestra di dialogo CorrelatesOn.

È possibile trascinare l'ActivityDesigner **Receive** dalla **casella degli strumenti** e rilasciarlo nell'area di progettazione flussi di lavoro, laddove le attività vengono in genere posizionate. Se si elimina l'ActivityDesigner, viene creata un' <xref:System.ServiceModel.Activities.Receive> attività con il valore predefinito <xref:System.Activities.Activity.DisplayName%2A> Receive. Per aprire la finestra di dialogo **definizione CorrelatesOn** , selezionare l'ActivityDesigner **Receive** , quindi nella griglia delle proprietà selezionare il pulsante con i puntini di sospensione accanto al testo della raccolta per la proprietà **CorrelatesOn** .

## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Activities.Receive>
- [Finestra di dialogo Aggiungi inizializzatori di correlazione](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Finestra di dialogo Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)