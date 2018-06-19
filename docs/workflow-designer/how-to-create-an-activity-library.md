---
title: 'Finestra di progettazione del flusso di lavoro - procedura: creare una libreria attività'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef62a5098581042a4995d6c522e0757c361e9d4f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974044"
---
# <a name="how-to-create-an-activity-library"></a>Procedura: creare una libreria attività
Le attività personalizzate sono usate per modellare i processi aziendali particolari in un flusso di lavoro. Il modello libreria di attività in Visual Studio 2010 è stato specificato per consentire la creazione di tali attività personalizzate usando visivamente la finestra di progettazione del flusso di lavoro di Windows.

### <a name="to-create-a-workflow-activity-library"></a>Per creare una libreria attività flussi di lavoro

1.  Avviare Visual Studio 2010.

2.  Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3.  Nel **tipi di progetto** riquadro, selezionare **flusso di lavoro** da uno di **Visual c#** progetti o **Visual Basic** raggruppamenti in base il preferenze della lingua.

4.  Nel **modelli** riquadro, selezionare **libreria attività**.

5.  Nel **nome** casella, digitare un nome descrittivo per il progetto per renderlo facilmente identificabile.

6.  Nel **percorso** casella, digitare la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale.

7.  Nel **soluzione** casella, digitare un nome descrittivo per la soluzione, quindi fare clic su **OK**.

    > [!NOTE]
    > Se si desidera aggiungere un'applicazione console flusso di lavoro a una soluzione esistente, aprire la soluzione in Visual Studio 2010, fare clic con il pulsante destro la soluzione in **Esplora soluzioni**e selezionare **Add**, quindi  **Nuovo progetto** per aprire la **nuovo progetto** finestra di dialogo. Procedere come descritto sopra in questa procedura.

8.  Il modello di progetto crea una definizione di attività in XAML. Progettazione del flusso di lavoro di Windows viene visualizzato nell'area di lavoro per l'attività personalizzata.

9. Trascinare un'attività dal **della casella degli strumenti** all'area di progettazione per includerla nell'attività personalizzata.

    > [!CAUTION]
    > È consentita una sola attività figlio nel corpo dell'attività personalizzata. L'attività in questione può tuttavia essere un oggetto CompositeActivity, quale <xref:System.Activities.Statements.Sequence> o <xref:System.Activities.Statements.Flowchart>.

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare un'attività](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)