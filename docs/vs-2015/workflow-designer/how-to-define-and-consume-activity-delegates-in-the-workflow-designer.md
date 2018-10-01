---
title: 'Procedura: definire e usare delegati di attività nella finestra di progettazione del flusso di lavoro | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 5bf6a53879e90dab2a0a57d99ee27d81bd1dfc35
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540597"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Procedura: definire e utilizzare delegati di attività in Progettazione del flusso di lavoro
In [!INCLUDE[net_v45](../includes/net-v45-md.md)] è inclusa una nuova finestra di progettazione predefinita dell'attività di <xref:System.Activities.Statements.InvokeDelegate>. Questa finestra di progettazione può essere usata per assegnare i delegati all'attività che derivano da <xref:System.Activities.ActivityDelegate>, come <xref:System.Activities.ActivityAction> o <xref:System.Activities.ActivityFunc%601>.  
  
### <a name="define-an-activity-delegate"></a>Definire un delegato dell'attività  
  
1.  Nelle [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], selezionare **File**, **New**, **progetto**. Selezionare il **flusso di lavoro** nodo a sinistra e il **applicazione Console flusso di lavoro** modello sul lato destro. Denominare il progetto (se lo si desidera) e fare clic su **accettabile**.  
  
2.  Pulsante destro del mouse sul progetto in **Esplora soluzioni** e selezionare **Add**, **nuovo elemento...** . Selezionare il **flusso di lavoro** nodo a sinistra e il **attività** modello sul lato destro. Denominare la nuova attività **Myforeach** e fare clic su **Ok**. L'attività verrà visualizzata nella finestra di progettazione flussi di lavoro.  
  
3.  Nella finestra di progettazione del flusso di lavoro, scegliere il **argomenti** scheda.  
  
4.  Fare clic su **Crea argomento**. Assegnare un nome al nuovo argomento **elementi**.  
  
5.  Nel **tipo di argomento** colonna, selezionare **matrice di T []**.  
  
6.  Nel browser dei tipi, selezionare **oggetto**. Fare clic su **accettabile**.  
  
7.  Fare clic su **Crea argomento** nuovamente. Assegnare un nome al nuovo argomento **corpo**. Nel **direzione** colonna per il nuovo argomento, selezionare **proprietà**.  
  
8.  Nella colonna tipo di argomento, selezionare **Cerca tipi...**  
  
9. Nel browser dei tipi, immettere **ActivityAction** nel **nome tipo** campo. Selezionare **ActivityAction\<T >** nella visualizzazione albero. Selezionare **oggetti** nell'elenco a discesa che viene visualizzato per assegnare il tipo **ActivityAction\<oggetto >** all'argomento.  
  
10. Trascinare un <xref:System.Activities.Statements.While> attività dal **flusso di controllo** sezione della casella degli strumenti all'area di progettazione.  
  
11. Selezionare il <xref:System.Activities.Statements.While> attività e selezionare il **variabili** scheda.  
  
12. Selezionare **creare variabile**. Denominare la nuova variabile **indice**.  
  
13. Nel **tipo di variabile** colonna, selezionare **Int32**. Lasciare il **ambito** come **mentre**e il **predefinito** colonna vuota.  
  
14. Impostare il **condizione** proprietà del <xref:System.Activities.Statements.While> attività **indice < Items.Length;**.  
  
15. Trascinare un' <xref:System.Activities.Statements.InvokeDelegate> attività dal **primitive** sezione della casella degli strumenti per il **corpo** del <xref:System.Activities.Statements.While> attività.  
  
16. Selezionare **corpo** nell'elenco a discesa delegato.  
  
17. Nel **delle proprietà** griglia per il <xref:System.Activities.Statements.InvokeDelegate> attività, fare clic sui **...** pulsante di **argomenti del delegato** proprietà.  
  
18. Nel **valore** colonna dell'argomento denominato **argomento**, immettere **Items [Index]**. Fare clic su **accettabile** per chiudere la **DelegateArguments** finestra di dialogo.  
  
19. Trascinare un'attività di <xref:System.Activities.Statements.Assign> sulla riga orizzontale al di sotto dell'attività di <xref:System.Activities.Statements.InvokeDelegate>. Il <xref:System.Activities.Statements.Assign> verrà creata l'attività e una <xref:System.Activities.Statements.Sequence> attività verrà creata automaticamente per contenere le due attività nel **corpo** sezione del **MyForEach** attività. La sequenza è necessaria poiché il **corpo** sezione può contenere solo una singola attività. La creazione automatica di una nuova attività <xref:System.Activities.Statements.Sequence> è una nuova funzionalità di [!INCLUDE[net_v45](../includes/net-v45-md.md)].  
  
20. Impostare il **a** proprietà del <xref:System.Activities.Statements.Assign> attività **indice**. Impostare il **valore** proprietà del **assegnare** attività **index+1**.  
  
 L'oggetto personalizzato **MyForEach** attività richiamerà un'attività arbitraria una volta per ogni valore passato tramite il **elementi** insieme con i valori nella raccolta come input per l'attività.  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>Usare l'attività personalizzata in un flusso di lavoro  
  
1.  Compilare il progetto premendo **Ctrl + MAIUSC + B**.  
  
2.  Nelle **Esplora soluzioni**aprire **Workflow1.xaml** nella finestra di progettazione.  
  
3.  Trascinare un **MyForEach** attività dalla casella degli strumenti all'area di progettazione. L'attività si troverà in una sezione della casella degli strumenti con lo stesso nome del progetto.  
  
4.  Impostare il **elementi** proprietà del **MyForEach** attività **new Object [] {1, "abc"}**.  
  
5.  Trascinare un <xref:System.Activities.Statements.WriteLine> attività dal **primitive** sezione della casella degli strumenti per il **Delegate: Body** sezione del **MyForEach** attività.  
  
6.  Impostare il **testo** proprietà del <xref:System.Activities.Statements.WriteLine> attività **argument**.  
  
 Quando il flusso di lavoro viene eseguito, nella console verrà visualizzato quanto segue:  
  
 **1**   
**abc**