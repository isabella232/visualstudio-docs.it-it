---
title: 'Procedura: creare una libreria attività | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9dec73d392dc6af74e5daef99bd6d306f7d58409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662748"
---
# <a name="how-to-create-an-activity-library"></a>Procedura: creare una libreria attività
Le attività personalizzate sono usate per modellare i processi aziendali particolari in un flusso di lavoro. Il modello Libreria attività in [!INCLUDE[vs2010](../includes/vs2010-md.md)] è stato fornito per consentire di creare tali attività personalizzate usando visivamente [!INCLUDE[wfd1](../includes/wfd1-md.md)].

### <a name="to-create-a-workflow-activity-library"></a>Per creare una libreria attività flussi di lavoro

1. Avviare [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Scegliere **nuovo**dal menu **file** , quindi selezionare **progetto.**

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. Nel riquadro **Tipi progetto** selezionare flusso di **lavoro** dai progetti **Visual C#** o **Visual Basic** raggruppamenti a seconda delle preferenze della lingua.

4. Nel riquadro **modelli** selezionare **libreria attività**.

5. Nella casella **nome** Digitare un nome descrittivo per il progetto per facilitarne l'identificazione.

6. Nella casella **percorso** Digitare la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale directory.

7. Nella casella **soluzione** Digitare un nome descrittivo per la soluzione, quindi fare clic su **OK**.

    > [!NOTE]
    > Se si desidera aggiungere un'applicazione console del flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../includes/vs2010-md.md)] , fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni**e selezionare **Aggiungi**, quindi **nuovo progetto.** per aprire la finestra di dialogo **nuovo progetto** . Procedere come descritto sopra in questa procedura.

8. Il modello di progetto crea una definizione di attività in XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] verrà visualizzato con l'area di disegno per l'attività personalizzata.

9. Trascinare un'attività dalla **casella degli strumenti** nell'area di progettazione per includerla nell'attività personalizzata.

    > [!CAUTION]
    > È consentita una sola attività figlio nel corpo dell'attività personalizzata. L'attività in questione può tuttavia essere un oggetto CompositeActivity, quale <xref:System.Activities.Statements.Sequence> o <xref:System.Activities.Statements.Flowchart>.

## <a name="see-also"></a>Vedere anche
 [Procedura: creare un'attività](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)