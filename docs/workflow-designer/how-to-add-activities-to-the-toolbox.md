---
title: 'Finestra di progettazione del flusso di lavoro - procedura: Aggiungere attività nella casella degli strumenti'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9e50736e5d9bc55eadf0aab7e7f00d26eb03249
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949593"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Procedura: Aggiungere attività nella casella degli strumenti

Le attività possono essere aggiunte per il **casella degli strumenti** nella soluzione in diversi modi. È possibile aggiungerli dall'interno il progetto corrente oppure fare riferimento a essi da un progetto diverso o da un assembly diverso.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Per aggiungere un'attività dall'interno del progetto corrente

1. Aggiungere una nuova attività personalizzata al progetto del flusso di lavoro corrente. Per altre informazioni sull'aggiunta di una nuova attività personalizzata al progetto, vedere [come: Aggiungere un nuovo elemento a un progetto di flusso di lavoro](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2. Aggiungere la logica personalizzata all'attività.

3. Compilare il progetto. Se la compilazione ha avuto esito positivo, una nuova categoria nella **casella degli strumenti** denominata "\<*nome progetto*>" viene visualizzato con l'attività personalizzata in essa inclusa.

    > [!NOTE]
    > Se la casella degli strumenti viene reimpostata, le attività personalizzate verranno rimosse, anche se la soluzione viene compilata nuovamente. Per ripopolare la casella degli strumenti con le attività personalizzate dopo che è stata reimpostata, riavviare Visual Studio.

    > [!NOTE]
    > La casella degli strumenti può mostrare solo un'attività di un nome specificato. Se due attività derivanti da assembly differenti hanno lo stesso nome della classe, solo una viene visualizzata.

    > [!NOTE]
    > Il dominio applicazione viene condiviso tra le istanze dell'editor; se vengono usate le variabili statiche, queste verranno condivise anche tra le istanze dell'editor. Se non si tratta del comportamento desiderato, un servizio deve essere usato per tenere traccia delle istanze variabili. Visualizzare [utilizzando il contesto di modifica ModelItem](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) per informazioni sull'uso di servizi all'interno della finestra di progettazione.

## <a name="to-add-an-activity-from-within-a-different-project"></a>Per aggiungere un'attività dall'interno di un altro progetto

1. Aprire una soluzione che contiene almeno un progetto flusso di lavoro e un progetto libreria attività personalizzato oppure un altro progetto flusso di lavoro che definisce un'attività personalizzata.

2. Compilare entrambi i progetti. Se la compilazione viene eseguita correttamente, una nuova categoria nella **casella degli strumenti** denominata "\<*nome progetto*>" viene visualizzato con l'attività personalizzata in essa inclusa.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Per aggiungere un'attività alla Casella degli strumenti da un assembly

1. Aprire una soluzione per flussi di lavoro.

2. Dal **degli strumenti** dal menu **Scegli elementi della casella degli strumenti**.

3. Nel **Scegli elementi della casella degli strumenti** finestra di dialogo, seleziona la **componenti System. Activities** scheda, quindi fare clic su **Sfoglia** per passare all'assembly che contiene l'oggetto personalizzato attività da aggiungere.

4. Selezionare l'assembly e fare clic su **OK**. Il componente attività personalizzata viene aggiunto all'elenco dei componenti e viene selezionato automaticamente.

    1. Fare clic su **OK** per chiudere la finestra di dialogo.

5. Per visualizzare la casella degli strumenti, selezionare **casella degli strumenti** dalle **visualizzazione** menu.

6. L'attività personalizzata viene visualizzato nei **casella degli strumenti** sotto la categoria che aveva lo stato attivo prima che l'elemento è stato aggiunto. Ad esempio, se il **generali** categoria è stata selezionata nella **della casella degli strumenti** prima di aggiungere l'elemento della casella degli strumenti, l'attività viene visualizzata sotto il **generale** categoria.

## <a name="see-also"></a>Vedere anche

- [Uso di Progettazione flussi di lavoro](developing-applications-with-the-workflow-designer.md)