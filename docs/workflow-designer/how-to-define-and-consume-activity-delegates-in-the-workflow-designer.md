---
title: Definire e usare delegati di attività
description: In Progettazione flussi di lavoro informazioni su come .NET Framework 4.5 include una finestra di progettazione predefinita per l'attività InvokeDelegate che è possibile usare per definire e utilizzare i delegati di attività.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 150b3b3ababe9e559cc8fe07d049509348201f08
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963565"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Procedura: definire e utilizzare delegati di attività in Progettazione del flusso di lavoro

.NET Framework 4.5 include una finestra di progettazione personalizzata per <xref:System.Activities.Statements.InvokeDelegate> l'attività. Questa finestra di progettazione può essere usata per assegnare i delegati all'attività che derivano da <xref:System.Activities.ActivityDelegate>, come <xref:System.Activities.ActivityAction> o <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Definire un delegato dell'attività

1. Creare un nuovo progetto **Applicazione console flusso di lavoro.**

   > [!NOTE]
   > Se i modelli di  progetto del flusso di lavoro non vengono visualizzati, installare prima **il Windows Workflow Foundation** di Visual Studio. Per istruzioni dettagliate, vedere [Installare Windows Workflow Foundation.](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)

3. Fare clic con il pulsante destro del mouse **sul progetto** Esplora soluzioni selezionare **Aggiungi**  >  **nuovo elemento**. Selezionare la **categoria Flusso** di lavoro e quindi selezionare il **modello elemento** Attività. Assegnare alla nuova attività **il nome MyForEach.xaml** e quindi selezionare **OK.**

   L'attività viene aperta nella finestra di progettazione del flusso di lavoro.

4. Nella finestra Progettazione flussi di lavoro fare clic sulla **scheda** Argomenti.

5. Fare clic su **Crea argomento**. Assegnare al nuovo argomento il **nome Items**.

6. Nella colonna **Tipo di** argomento selezionare Matrice **di [T]**.

7. Nel browser dei tipi selezionare **Oggetto** e quindi **selezionare OK.**

8. Fare **di nuovo clic su Crea** argomento. Assegnare al nuovo argomento il nome **Body**. Nella colonna **Direzione** per il nuovo argomento selezionare **Proprietà**.

9. Nella colonna Tipo di argomento selezionare **Sfoglia per i tipi**

10. Nel browser dei tipi immettere **ActivityAction** nel **campo Nome** tipo. Selezionare **ActivityAction \<T>** nella visualizzazione albero. Selezionare **Oggetto** nell'elenco a discesa visualizzato per assegnare il tipo **ActivityAction \<Object>** all'argomento.

11. Trascinare <xref:System.Activities.Statements.While> un'attività dalla **sezione Controllo Flow** della casella degli strumenti all'area di progettazione.

12. Selezionare <xref:System.Activities.Statements.While> l'attività e selezionare la **scheda** Variabili.

13. Selezionare **Crea variabile**. Assegnare alla nuova variabile il nome **Index**.

14. Nella colonna **Tipo variabile** selezionare **Int32**. Lasciare vuoto **Ambito** come **While** e **la colonna** Default.

15. Impostare la **proprietà Condition** dell'attività su index <xref:System.Activities.Statements.While> < **Items.Length;**.

16. Trascinare <xref:System.Activities.Statements.InvokeDelegate> un'attività **dalla sezione Primitive** della casella degli strumenti al **corpo** <xref:System.Activities.Statements.While> dell'attività.

17. Selezionare **Corpo** nell'elenco a discesa del delegato.

18. Nella griglia **Proprietà** per l'attività <xref:System.Activities.Statements.InvokeDelegate> fare clic sul pulsante **...** nella proprietà **Argomenti delegato** .

19. Nella colonna **Valore** dell'argomento denominato **Argument** immettere **Items[Index]**. Fare **clic su OK** per chiudere la finestra di dialogo **DelegateArguments.**

20. Trascinare un'attività di <xref:System.Activities.Statements.Assign> sulla riga orizzontale al di sotto dell'attività di <xref:System.Activities.Statements.InvokeDelegate>. L'attività viene creata e viene creata automaticamente un'attività per contenere le due attività nella <xref:System.Activities.Statements.Assign> <xref:System.Activities.Statements.Sequence> sezione **Corpo** dell'attività **MyForEach.** La sequenza è necessaria perché la **sezione Corpo** può contenere solo una singola attività. La creazione automatica di <xref:System.Activities.Statements.Sequence> una nuova attività è una nuova funzionalità di .NET Framework 4.5.

21. Impostare la **proprietà To** dell'attività <xref:System.Activities.Statements.Assign> su **index**. Impostare la **proprietà Value** dell'attività **Assign** su **index+1.**

    **L'attività MyForEach** personalizzata richiama un'attività arbitraria una volta per ogni valore passato tramite la raccolta **Items,** con i valori nella raccolta come input per l'attività.

## <a name="use-the-custom-activity-in-a-workflow"></a>Usare l'attività personalizzata in un flusso di lavoro

1. Compilare il progetto premendo **CTRL** + **MAIUSC** + **B.**

2. In **Esplora soluzioni** aprire **Workflow1.xaml** nella finestra di progettazione.

3. Trascinare **un'attività MyForEach** dalla casella degli strumenti all'area di progettazione. L'attività si trova in una sezione della casella degli strumenti con lo stesso nome del progetto.

4. Impostare la **proprietà Items** dell'attività **MyForEach** su **new Object[] {1, "abc"}**.

5. Trascinare <xref:System.Activities.Statements.WriteLine> un'attività **dalla sezione Primitives** della casella degli strumenti alla sezione **Delegate:Body** dell'attività **MyForEach.**

6. Impostare la **proprietà Text** dell'attività <xref:System.Activities.Statements.WriteLine> su **Argument.ToString()**.

Quando viene eseguito il flusso di lavoro, nella console viene visualizzato l'output seguente:

**1** 
 **abc**
