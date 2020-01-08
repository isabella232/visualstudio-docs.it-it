---
title: 'Progettazione flussi di lavoro-procedura: aggiungere attività alla casella degli strumenti'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3cde4f3a41a1a07f982f85c0c19e9f16b047068
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593928"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Procedura: aggiungere attività nella Casella degli strumenti

Le attività possono essere aggiunte alla **casella degli strumenti** nella soluzione in diversi modi. È possibile aggiungerli dall'interno il progetto corrente oppure fare riferimento a essi da un progetto diverso o da un assembly diverso.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Per aggiungere un'attività dall'interno del progetto corrente

1. Aggiungere una nuova attività personalizzata al progetto del flusso di lavoro corrente. Per ulteriori informazioni sull'aggiunta di una nuova attività personalizzata al progetto, vedere [procedura: aggiungere un nuovo elemento a un progetto flusso di lavoro](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2. Aggiungere la logica personalizzata all'attività.

3. Compilazione del progetto. Se la compilazione ha avuto esito positivo, viene visualizzata una nuova categoria nella **casella degli strumenti** denominata "\<*nome progetto*>" con l'attività personalizzata inclusa in tale categoria.

    > [!NOTE]
    > Se la casella degli strumenti viene reimpostata, le attività personalizzate verranno rimosse, anche se la soluzione viene compilata nuovamente. Per ripopolare la casella degli strumenti con attività personalizzate dopo che è stata reimpostata, riavviare Visual Studio.

    > [!NOTE]
    > La casella degli strumenti può mostrare solo un'attività di un nome specificato. Se due attività derivanti da assembly differenti hanno lo stesso nome della classe, solo una viene visualizzata.

    > [!NOTE]
    > Il dominio applicazione viene condiviso tra le istanze dell'editor; se vengono usate le variabili statiche, queste verranno condivise anche tra le istanze dell'editor. Se non si tratta del comportamento desiderato, un servizio deve essere usato per tenere traccia delle istanze variabili. Per informazioni sull'uso dei servizi all'interno della finestra di progettazione, vedere [utilizzo del contesto di modifica ModelItem](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) .

## <a name="to-add-an-activity-from-within-a-different-project"></a>Per aggiungere un'attività dall'interno di un altro progetto

1. Aprire una soluzione che contiene almeno un progetto flusso di lavoro e un progetto libreria attività personalizzato oppure un altro progetto flusso di lavoro che definisce un'attività personalizzata.

2. Compilare entrambi i progetti. Se le compilazioni sono state completate correttamente, viene visualizzata una nuova categoria nella **casella degli strumenti** denominata "\<*nome progetto*>" con l'attività personalizzata inclusa in tale categoria.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Per aggiungere un'attività alla Casella degli strumenti da un assembly

1. Aprire una soluzione per flussi di lavoro.

2. **Scegliere Scegli elementi della casella degli**strumenti dal menu **strumenti** .

3. Nella finestra di dialogo **Scegli elementi della casella degli strumenti** selezionare la scheda **componenti System. Activities** , quindi fare clic su **Sfoglia** per passare all'assembly che contiene l'attività personalizzata che si desidera aggiungere.

4. Selezionare l'assembly e fare clic su **OK**. Il componente attività personalizzata viene aggiunto all'elenco dei componenti e viene selezionato automaticamente.

    1. Fare clic su **OK** per chiudere la finestra di dialogo.

5. Per visualizzare la casella degli strumenti, scegliere **casella degli strumenti** dal menu **Visualizza** .

6. L'attività personalizzata viene visualizzata nella **casella degli strumenti** sotto la categoria che era attiva prima dell'aggiunta dell'elemento. Se, ad esempio, la categoria **generale** è stata selezionata nella **casella degli strumenti** prima di aggiungere l'elemento della casella degli strumenti, l'attività viene visualizzata sotto la categoria **generale** .

## <a name="see-also"></a>Vedere anche

- [Uso di Progettazione flussi di lavoro](developing-applications-with-the-workflow-designer.md)
