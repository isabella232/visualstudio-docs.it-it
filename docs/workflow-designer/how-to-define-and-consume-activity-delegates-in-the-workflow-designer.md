---
title: 'Finestra di progettazione del flusso di lavoro - procedura: Definire e usare delegati di attività'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 95aede6217bca263be7edd7440cc5e9bb23e25ab
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53908462"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Procedura: Definire e usare delegati di attività in Progettazione flussi di lavoro

.NET framework 4.5 include una finestra di progettazione di out-of-box per il <xref:System.Activities.Statements.InvokeDelegate> attività. Questa finestra di progettazione può essere usata per assegnare i delegati all'attività che derivano da <xref:System.Activities.ActivityDelegate>, come <xref:System.Activities.ActivityAction> o <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Definire un delegato dell'attività

1. In Visual Studio selezionare **File** > **Nuovo** > **Progetto**.

2. Nel **nuovo progetto** finestra di dialogo, seleziona la **flusso di lavoro** categoria a sinistra e quindi selezionare il **applicazione Console flusso di lavoro** modello di progetto. Denominare il progetto (se lo si desidera) e fare clic su **accettabile**.

   > [!NOTE]
   > Se non viene visualizzato il **flusso di lavoro** category, installare prima il **Windows Workflow Foundation** componente di Visual Studio 2017. Per istruzioni dettagliate, vedere [installazione di Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. Pulsante destro del mouse sul progetto in **Esplora soluzioni** e selezionare **Add** > **nuovo elemento**. Selezionare il **flusso di lavoro** categoria e quindi selezionare la **attività** modello di elemento. Denominare la nuova attività **Myforeach** e quindi selezionare **OK**.

   L'attività viene aperto nella finestra di progettazione del flusso di lavoro.

4. Nella finestra di progettazione del flusso di lavoro, scegliere il **argomenti** scheda.

5. Fare clic su **Crea argomento**. Assegnare un nome al nuovo argomento **elementi**.

6. Nel **tipo di argomento** colonna, selezionare **matrice di T []**.

7. Nel browser dei tipi, selezionare **oggetti** e quindi selezionare **OK**.

8. Fare clic su **Crea argomento** nuovamente. Assegnare un nome al nuovo argomento **corpo**. Nel **direzione** colonna per il nuovo argomento, selezionare **proprietà**.

9. Nella colonna tipo di argomento, selezionare **Cerca tipi**

10. Nel browser dei tipi, immettere **ActivityAction** nel **nome tipo** campo. Selezionare **ActivityAction\<T >** nella visualizzazione albero. Selezionare **oggetti** nell'elenco a discesa che viene visualizzato per assegnare il tipo **ActivityAction\<oggetto >** all'argomento.

11. Trascinare un <xref:System.Activities.Statements.While> attività dal **flusso di controllo** sezione della casella degli strumenti all'area di progettazione.

12. Selezionare il <xref:System.Activities.Statements.While> attività e selezionare il **variabili** scheda.

13. Selezionare **creare variabile**. Denominare la nuova variabile **indice**.

14. Nel **tipo di variabile** colonna, selezionare **Int32**. Lasciare il **ambito** come **mentre**e il **predefinito** colonna vuota.

15. Impostare il **condizione** proprietà del <xref:System.Activities.Statements.While> attività **indice < Items.Length;**.

16. Trascinare un' <xref:System.Activities.Statements.InvokeDelegate> attività dal **primitive** sezione della casella degli strumenti per il **corpo** del <xref:System.Activities.Statements.While> attività.

17. Selezionare **corpo** nell'elenco a discesa delegato.

18. Nel **delle proprietà** griglia per il <xref:System.Activities.Statements.InvokeDelegate> attività, fare clic sui **...**  pulsante il **argomenti del delegato** proprietà.

19. Nel **valore** colonna dell'argomento denominato **argomento**, immettere **Items [Index]**. Fare clic su **accettabile** per chiudere la **DelegateArguments** finestra di dialogo.

20. Trascinare un'attività di <xref:System.Activities.Statements.Assign> sulla riga orizzontale al di sotto dell'attività di <xref:System.Activities.Statements.InvokeDelegate>. Il <xref:System.Activities.Statements.Assign> creazione di attività e un <xref:System.Activities.Statements.Sequence> attività viene creato automaticamente per contenere le due attività nel **corpo** sezione del **MyForEach** attività. La sequenza è necessaria poiché il **corpo** sezione può contenere solo una singola attività. Creazione automatica di un nuovo <xref:System.Activities.Statements.Sequence> attività è una nuova funzionalità di .NET Framework 4.5.

21. Impostare il **a** proprietà del <xref:System.Activities.Statements.Assign> attività **indice**. Impostare il **valore** proprietà del **assegnare** attività **index+1**.

    L'oggetto personalizzato **MyForEach** attività richiama un'attività arbitraria una volta per ogni valore passato tramite il **elementi** insieme con i valori nella raccolta come input per l'attività.

## <a name="use-the-custom-activity-in-a-workflow"></a>Usare l'attività personalizzata in un flusso di lavoro

1.  Compilare il progetto premendo **Ctrl**+**MAIUSC**+**B**.

2.  Nelle **Esplora soluzioni**aprire **Workflow1.xaml** nella finestra di progettazione.

3.  Trascinare un **MyForEach** attività dalla casella degli strumenti all'area di progettazione. L'attività è in una sezione della casella degli strumenti con lo stesso nome del progetto.

4.  Impostare il **elementi** proprietà del **MyForEach** attività **new Object [] {1, "abc"}**.

5.  Trascinare un <xref:System.Activities.Statements.WriteLine> attività dal **primitive** sezione della casella degli strumenti per il **Delegate: Body** sezione del **MyForEach** attività.

6.  Impostare il **testo** proprietà del <xref:System.Activities.Statements.WriteLine> attività **argument**.

Quando viene eseguito il flusso di lavoro, la console Mostra l'output seguente:

**1**
**abc**