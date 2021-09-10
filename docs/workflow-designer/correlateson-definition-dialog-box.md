---
title: Progettazione flussi di lavoro finestra di dialogo CorrelatesOn Definition
description: Informazioni su come usare la finestra di dialogo CorrelatesOn Progettazione flussi di lavoro modificare la proprietà CorrelatesOn di un'attività Receive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 0b0730853bb2f7e67445a85c4a05d6adbfc22dc3
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963403"
---
# <a name="correlateson-definition-dialog-box"></a>Finestra di dialogo Definizione di CorrelatesOn

La **finestra di dialogo CorrelatesOn** viene usata Progettazione flussi di lavoro per modificare la proprietà di <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> <xref:System.ServiceModel.Activities.Receive> un'attività. Per altre informazioni, vedere [Receive ActivityDesigner](../workflow-designer/receive-activity-designer.md).

La correlazione tra le attività <xref:System.ServiceModel.Activities.Receive> specifica come operazioni del servizio diverse si connettono tra loro in un flusso di lavoro.

Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente della finestra di dialogo **CorrelatesOn.**

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**CorrelatesWith**|Oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per indirizzare il messaggio all'istanza del flusso di lavoro appropriata.|
|**Query XPath**|Una coppia chiave/valore che contiene le query usate per estrarre dati di correlazione dai messaggi in ingresso. Questo valore corrisponde alla <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> proprietà . Le query XPath sono incluse in un oggetto <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Per aprire la finestra di dialogo CorrelatesOn.

**L'ActivityDesigner** di ricezione  può essere trascinato dalla casella degli strumenti e rilasciato nell'area Progettazione flussi di lavoro, ovunque le attività siano in genere posizionate. L'eliminazione dell'ActivityDesigner crea <xref:System.ServiceModel.Activities.Receive> un'attività con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito Receive. Per aprire la finestra di dialogo  Definizione **CorrelatesOn,** selezionare l'ActivityDesigner ricezione e quindi nella griglia delle proprietà selezionare il pulsante con i puntini di sospensione accanto al testo raccolta per la **proprietà CorrelatesOn.**

## <a name="see-also"></a>Vedi anche

- <xref:System.ServiceModel.Activities.Receive>
- [Finestra di dialogo Aggiungi inizializzatori di correlazione](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Finestra di dialogo Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)