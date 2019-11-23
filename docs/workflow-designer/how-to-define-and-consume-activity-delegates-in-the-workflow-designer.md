---
title: 'Progettazione flussi di lavoro: definire e utilizzare delegati di attività'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 67e862e3772b157c4a0999ccd44c3698119ae8a8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650341"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Procedura: definire e utilizzare delegati di attività in Progettazione del flusso di lavoro

.NET Framework 4,5 include una finestra di progettazione predefinita per l'attività <xref:System.Activities.Statements.InvokeDelegate>. Questa finestra di progettazione può essere usata per assegnare i delegati all'attività che derivano da <xref:System.Activities.ActivityDelegate>, come <xref:System.Activities.ActivityAction> o <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Definire un delegato dell'attività

1. Creare un nuovo progetto di **applicazione console del flusso di lavoro** .

   > [!NOTE]
   > Se non vengono visualizzati i modelli di progetto del **flusso di lavoro** , installare prima il componente **Windows Workflow Foundation** di Visual Studio. Per istruzioni dettagliate, vedere [Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Aggiungi** > **nuovo elemento**. Selezionare la categoria **flusso di lavoro** , quindi selezionare il modello di elemento di **attività** . Assegnare alla nuova attività il nome **foreach. XAML** e quindi selezionare **OK**.

   L'attività viene aperta nella finestra di progettazione del flusso di lavoro.

4. Nella Progettazione flussi di lavoro fare clic sulla scheda **argomenti** .

5. Fare clic su **Crea argomento**. Denominare i nuovi **elementi**argomento.

6. Nella colonna **tipo di argomento** selezionare **matrice di [T]** .

7. Nel browser dei tipi selezionare **oggetto** e quindi fare clic su **OK**.

8. Fare di nuovo clic su **Crea argomento** . Denominare il nuovo **corpo**dell'argomento. Nella colonna **direzione** del nuovo argomento selezionare **Proprietà**.

9. Nella colonna tipo di argomento selezionare **Cerca tipi**

10. Nel browser dei tipi immettere **ActivityAction** nel campo **nome tipo** . Selezionare **ActivityAction\<t >** nella visualizzazione albero. Selezionare **oggetto** nell'elenco a discesa che viene visualizzato per assegnare il tipo **ActivityAction\<oggetto >** all'argomento.

11. Trascinare un'attività <xref:System.Activities.Statements.While> dalla sezione **flusso di controllo** della casella degli strumenti all'area di progettazione.

12. Selezionare l'attività <xref:System.Activities.Statements.While> e selezionare la scheda **variabili** .

13. Selezionare **Crea variabile**. Assegnare un nome al nuovo **Indice**della variabile.

14. Nella colonna **tipo di variabile** selezionare **Int32**. Lasciare l' **ambito** come **while**e la colonna **default** blank.

15. Impostare la proprietà **Condition** dell'attività <xref:System.Activities.Statements.While> su **index < Items. length;** .

16. Trascinare un'attività <xref:System.Activities.Statements.InvokeDelegate> dalla sezione **primitive** della casella degli strumenti al **corpo** dell'attività <xref:System.Activities.Statements.While>.

17. Selezionare **corpo** nell'elenco a discesa delegato.

18. Nella griglia delle **Proprietà** per l'attività <xref:System.Activities.Statements.InvokeDelegate> fare clic sul pulsante **...** nella proprietà **argomenti del delegato** .

19. Nella colonna **valore** dell'argomento denominato **argument**immettere **Items [index]** . Fare clic su **OK** per chiudere la finestra di dialogo **DelegateArguments** .

20. Trascinare un'attività di <xref:System.Activities.Statements.Assign> sulla riga orizzontale al di sotto dell'attività di <xref:System.Activities.Statements.InvokeDelegate>. Viene creata l'attività <xref:System.Activities.Statements.Assign> e viene creata automaticamente un'attività <xref:System.Activities.Statements.Sequence> per contenere le due attività nella sezione **Body** dell'attività **foreach** . La sequenza è necessaria perché la sezione **Body** può contenere solo una singola attività. La creazione automatica di una nuova attività <xref:System.Activities.Statements.Sequence> è una nuova funzionalità di .NET Framework 4,5.

21. Impostare la proprietà **su** dell'attività <xref:System.Activities.Statements.Assign> su **index**. Impostare la proprietà **value** dell'attività **assign** su **index + 1**.

    L'attività **foreach** personalizzata richiama un'attività arbitraria una volta per ogni valore passato attraverso la raccolta **Items** , con i valori nella raccolta come input per l'attività.

## <a name="use-the-custom-activity-in-a-workflow"></a>Usare l'attività personalizzata in un flusso di lavoro

1. Compilare il progetto premendo **Ctrl**+**MAIUSC**+**B**.

2. In **Esplora soluzioni**aprire **Workflow1. XAML** nella finestra di progettazione.

3. Trascinare un'attività **foreach** dalla casella degli strumenti all'area di progettazione. L'attività si trova in una sezione della casella degli strumenti con lo stesso nome del progetto.

4. Impostare la proprietà **Items** dell'attività **foreach** su **New Object [] {1, "ABC"}** .

5. Trascinare un'attività <xref:System.Activities.Statements.WriteLine> dalla sezione **primitive** della casella degli strumenti alla sezione **delegate: Body** dell'attività **foreach** .

6. Impostare la proprietà **Text** dell'attività <xref:System.Activities.Statements.WriteLine> su **argument. ToString ()** .

Quando il flusso di lavoro viene eseguito, nella console viene visualizzato l'output seguente:

**1**
**abc**