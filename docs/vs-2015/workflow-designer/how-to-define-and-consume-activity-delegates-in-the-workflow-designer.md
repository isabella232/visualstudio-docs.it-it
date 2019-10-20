---
title: "Procedura: definire e utilizzare delegati di attività nell'Progettazione flussi di lavoro | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26ba92a2ba7aa6eed471383c875104549e896804
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603859"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Procedura: definire e utilizzare delegati di attività in Progettazione del flusso di lavoro
In [!INCLUDE[net_v45](../includes/net-v45-md.md)] è inclusa una nuova finestra di progettazione predefinita dell'attività di <xref:System.Activities.Statements.InvokeDelegate>. Questa finestra di progettazione può essere usata per assegnare i delegati all'attività che derivano da <xref:System.Activities.ActivityDelegate>, come <xref:System.Activities.ActivityAction> o <xref:System.Activities.ActivityFunc%601>.

### <a name="define-an-activity-delegate"></a>Definire un delegato dell'attività

1. In [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] selezionare **file**, **nuovo**, **progetto**. Selezionare il nodo **flusso di lavoro** a sinistra e il modello **applicazione console flusso di lavoro** a destra. Denominare il progetto (se necessario) e fare clic su **OK**.

2. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Aggiungi**, **nuovo elemento...** . Selezionare il nodo **flusso di lavoro** a sinistra e il modello **attività** a destra. Assegnare alla nuova attività il nome **foreach. XAML** e fare clic su **OK**. L'attività verrà visualizzata nella finestra di progettazione flussi di lavoro.

3. Nella finestra di progettazione del flusso di lavoro fare clic sulla scheda **argomenti** .

4. Fare clic su **Crea argomento**. Denominare i nuovi **elementi**argomento.

5. Nella colonna **tipo di argomento** selezionare **matrice di [T]** .

6. Nel browser dei tipi selezionare **oggetto**. Fare clic su **OK**.

7. Fare di nuovo clic su **Crea argomento** . Denominare il nuovo **corpo**dell'argomento. Nella colonna **direzione** del nuovo argomento selezionare **Proprietà**.

8. Nella colonna tipo di argomento selezionare **Cerca tipi...**

9. Nel browser dei tipi immettere **ActivityAction** nel campo **nome tipo** . Selezionare **ActivityAction \<T >** nella visualizzazione albero. Selezionare **oggetto** nell'elenco a discesa a cui viene assegnato il tipo **ActivityAction \<Object >** all'argomento.

10. Trascinare un'attività <xref:System.Activities.Statements.While> dalla sezione **flusso di controllo** della casella degli strumenti all'area di progettazione.

11. Selezionare l'attività <xref:System.Activities.Statements.While> e selezionare la scheda **variabili** .

12. Selezionare **Crea variabile**. Assegnare un nome al nuovo **Indice**della variabile.

13. Nella colonna **tipo di variabile** selezionare **Int32**. Lasciare l' **ambito** come **while**e la colonna **default** blank.

14. Impostare la proprietà **Condition** dell'attività <xref:System.Activities.Statements.While> su **index < Items. length;** .

15. Trascinare un'attività <xref:System.Activities.Statements.InvokeDelegate> dalla sezione **primitive** della casella degli strumenti al **corpo** dell'attività <xref:System.Activities.Statements.While>.

16. Selezionare **corpo** nell'elenco a discesa delegato.

17. Nella griglia delle **Proprietà** per l'attività <xref:System.Activities.Statements.InvokeDelegate> fare clic su **...** nella proprietà degli **argomenti del delegato** .

18. Nella colonna **valore** dell'argomento denominato **argument**immettere **Items [index]** . Fare clic su **OK** per chiudere la finestra di dialogo **DelegateArguments** .

19. Trascinare un'attività di <xref:System.Activities.Statements.Assign> sulla riga orizzontale al di sotto dell'attività di <xref:System.Activities.Statements.InvokeDelegate>. Verrà creata l'attività <xref:System.Activities.Statements.Assign> e verrà creata automaticamente un'attività <xref:System.Activities.Statements.Sequence> per contenere le due attività nella sezione **Body** dell'attività **foreach** . La sequenza è necessaria perché la sezione **Body** può contenere solo una singola attività. La creazione automatica di una nuova attività <xref:System.Activities.Statements.Sequence> è una nuova funzionalità di [!INCLUDE[net_v45](../includes/net-v45-md.md)].

20. Impostare la proprietà **su** dell'attività <xref:System.Activities.Statements.Assign> su **index**. Impostare la proprietà **value** dell'attività **assign** su **index + 1**.

    L'attività **foreach** personalizzata richiama ora un'attività arbitraria una volta per ogni valore passato attraverso la raccolta **Items** , con i valori nella raccolta come input per l'attività.

### <a name="use-the-custom-activity-in-a-workflow"></a>Usare l'attività personalizzata in un flusso di lavoro

1. Compilare il progetto premendo **CTRL + MAIUSC + B**.

2. In **Esplora soluzioni**aprire **Workflow1. XAML** nella finestra di progettazione.

3. Trascinare un'attività **foreach** dalla casella degli strumenti all'area di progettazione. L'attività si troverà in una sezione della casella degli strumenti con lo stesso nome del progetto.

4. Impostare la proprietà **Items** dell'attività **foreach** su **New Object [] {1, "ABC"}** .

5. Trascinare un'attività <xref:System.Activities.Statements.WriteLine> dalla sezione **primitive** della casella degli strumenti alla sezione **delegate: Body** dell'attività **foreach** .

6. Impostare la proprietà **Text** dell'attività <xref:System.Activities.Statements.WriteLine> su **argument. ToString ()** .

   Quando il flusso di lavoro viene eseguito, nella console verrà visualizzato quanto segue:

   **1** 
   **ABC**