---
title: "Procedura dettagliata: debug di un'applicazione multithread | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multithreaded debugging, walkthrough
- walkthroughs, multithreaded debugging
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33ce391523a256bcb195deccf0c14868b5eae707
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683090"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>Procedura dettagliata: debug di un'applicazione multithreading
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] fornisce una finestra **thread** migliorata e altri miglioramenti dell'interfaccia utente per semplificare il debug delle applicazioni multithreading. Il completamento di questa procedura dettagliata richiede solo alcuni minuti, ma è utile per familiarizzare con le nuove funzionalità dell'interfaccia per il debug delle applicazioni multithreading.  
  
 Per iniziare questa procedura dettagliata, è necessario un progetto di applicazione multithreading. Per creare tale progetto, attenersi alla procedura qui indicata.  
  
#### <a name="to-create-the-walkthrough-project"></a>Per creare il progetto necessario per la procedura dettagliata  
  
1. Scegliere **nuovo** dal menu **file** , quindi fare clic su **progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2. Nella casella **tipo di progetto**fare clic sulla lingua desiderata: **Visual Basic**, **Visual C#** o **Visual C++**.  
  
3. Nella casella **modelli** scegliere **applicazione console** o **applicazione console CLR**.  
  
4. Nella casella **nome** Digitare il nome MyThreadWalkthroughApp.  
  
5. Fare clic su **OK**.  
  
     Verrà visualizzato un nuovo progetto console. Dopo aver creato il progetto, viene visualizzato un file di origine. A seconda del linguaggio scelto, il nome del file di origine potrebbe essere Module1.vb, Program.cs o MyThreadWalkthroughApp.cpp  
  
6. Eliminare il codice visualizzato nel file di origine e sostituirlo con il codice di esempio visualizzato nella sezione "creazione di un thread" dell'argomento Creazione di [thread e passaggio di dati all'ora di inizio](https://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d).  
  
7. Scegliere **Salva tutti** dal menu **File**.  
  
#### <a name="to-begin-the-walkthrough"></a>Per iniziare la procedura dettagliata  
  
- Nella finestra di origine cercare il codice seguente:  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```csharp  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### <a name="to-start-debugging"></a>Per avviare il debug  
  
1. Fare clic con il pulsante destro del mouse sull' `Console.WriteLine` istruzione, scegliere punto di **interruzione** , quindi scegliere **Inserisci**punto di interruzione.  
  
     All'estrema sinistra della finestra di origine viene visualizzata una sfera rossa che indica l'impostazione di un punto di interruzione in tale posizione.  
  
2. Scegliere **Avvia debug** dal menu **Debug**.  
  
     Viene avviato il debug e viene avviata l'esecuzione dell'applicazione che viene quindi interrotta in corrispondenza del punto di interruzione.  
  
3. Se a questo punto la finestra dell'applicazione console ha lo stato attivo, fare clic nella finestra di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per ripristinare lo stato attivo di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. Nella finestra di origine trovare la riga che contiene il codice seguente:  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```csharp  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
1. 
  
#### <a name="to-discover-the-thread-marker"></a>Per individuare il marcatore del thread  
  
1. Fare clic con il pulsante destro del mouse nella finestra **thread** , quindi scegliere **Mostra thread nell'origine**.  
  
2. All'estrema sinistra della finestra, in corrispondenza di questa riga, verrà visualizzata un'icona con due fili, uno rosso e uno blu. Il marcatore del thread indica l'interruzione di un thread in questa posizione. È possibile, pertanto, che un thread venga interrotto in questa posizione.  
  
3. Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un suggerimento dati in cui è indicato il nome e il numero ID di ciascun thread interrotto. In questo caso, l'interruzione si è verificata in un solo thread denominato `<noname>`.  
  
4. Fare clic con il pulsante destro del mouse sul marcatore del thread per visualizzare un menu di scelta rapida.  
  
   Questa icona è un *marcatore di thread*:  
  
   ![Marcatore del thread](../debugger/media/threadmarker.gif "ThreadMarker")  
  
## <a name="flagging-and-unflagging-threads"></a>Impostazione e rimozione dei flag dei thread  
 In [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] è possibile impostare i flag dei thread a cui si desidera attribuire particolare attenzione. L'impostazione dei flag dei thread è un ottimo strumento per tenere traccia dei thread importanti e per ignorare quelli a cui non si desidera prestare attenzione.  
  
#### <a name="to-flag-threads"></a>Per impostare i flag dei thread  
  
1. Scegliere **barre degli strumenti**dal menu **Visualizza** .  
  
     Assicurarsi che la barra degli strumenti **posizione di debug** sia selezionata.  
  
2. Passare alla barra degli strumenti **posizione di debug** e fare clic sull'elenco **thread** .  
  
    > [!NOTE]
    > È possibile riconoscere questa barra degli strumenti per tre elenchi principali: **processo**, **thread**e **stack frame**.  
  
3. Osservare il numero di thread visualizzati nell'elenco.  
  
4. Tornare alla finestra di origine e fare di nuovo clic con il pulsante destro del mouse sul marcatore del **thread** .  
  
5. Scegliere **flag**dal menu di scelta rapida, quindi fare clic sul nome e sul numero ID del thread.  
  
6. Tornare alla barra degli strumenti **posizione di debug** e fare nuovamente clic sull'elenco **thread** .  
  
     Nell'elenco viene visualizzato ora solo il thread con flag. Pulsante del flag che si trova a destra dell'elenco dei **thread** . L'icona del flag sul pulsante che prima era visualizzata in grigio è ora di colore rosso.  
  
7. Posizionare il puntatore del mouse sull'icona del flag.  
  
     Viene visualizzato un popup Questa finestra popup indica la modalità in cui si trova l'elenco dei **thread** : **Mostra solo i thread con flag**.  
  
8. Fare clic sul pulsante flag per visualizzare di nuovo la modalità **Mostra tutti i thread** .  
  
9. Fare nuovamente clic sull'elenco **thread** e verificare che ora sia possibile visualizzare di nuovo tutti i thread.  
  
10. Fare clic sul pulsante flag per tornare indietro per **visualizzare solo i thread**con flag.  
  
11. Scegliere **Finestre** dal menu **Debug**, quindi **Thread**.  
  
     Verrà visualizzata la finestra **thread** . in cui è presente un thread con un'icona del flag associata.  
  
12. Nella finestra di origine fare nuovamente clic con il pulsante destro del mouse sul marcatore del thread.  
  
     Osservare ora le scelte disponibili nel menu di scelta rapida. Al posto del **flag**, viene ora visualizzato Rimuovi **flag**. Non fare clic su **Rimuovi flag**.  
  
13. Passare alla procedura successiva in cui viene descritto come rimuovere i flag dei thread.  
  
#### <a name="to-unflag-threads"></a>Per rimuovere i flag dei thread  
  
1. Nella finestra **thread** fare clic con il pulsante destro del mouse sulla riga corrispondente al thread contrassegnato.  
  
     Verrà visualizzato un menu di scelta rapida. Sono disponibili opzioni per la **deflag** e la **deflaging di tutti**.  
  
2. Per decontrassegnare il thread, fare clic su **Rimuovi flag**.  
  
3. Fare clic sull'icona del flag rossa.  
  
4. Esaminare di nuovo la barra degli strumenti **posizione di debug** . Il pulsante del flag è nuovamente in grigio. È stato rimosso il flag dall'unico thread con flag. Poiché non sono presenti thread contrassegnati, la barra degli strumenti è tornata per **mostrare la modalità tutti i thread** . Fare clic sull'elenco **thread** e verificare che sia possibile visualizzare tutti i thread.  
  
5. Tornare alla finestra **thread** ed esaminare le colonne di informazioni.  
  
     La maggior parte dei pulsanti situati all'inizio di ogni colonna dispone di titoli che identificano la colonna. Nella prima colonna a sinistra però non è presente alcun titolo, bensì un'icona con il profilo di una bandiera. Si noterà lo stesso profilo in ogni riga dell'elenco di thread. Il profilo indica la rimozione del flag del thread.  
  
6. Fare clic sui profili di due thread, il secondo e terzo dalla fine dell'elenco.  
  
     Le icone del flag con profili vuoti vengono sostituite da icone di colore rosso.  
  
7. Fare clic sul pulsante nella parte superiore della colonna dei flag.  
  
     Quando si fa clic su questo pulsante, cambia l'ordine dell'elenco di thread visualizzando ora i thread con flag all'inizio.  
  
8. Fare nuovamente clic sul pulsante nella parte superiore della colonna dei flag.  
  
     L'ordine cambia di nuovo.  
  
## <a name="more-about-the-threads-window"></a>Ulteriori informazioni sulla finestra Thread  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Per ulteriori informazioni sulla finestra Thread  
  
1. Nella finestra **thread** esaminare la terza colonna da sinistra. Il pulsante nella parte superiore della colonna indica **ID**.  
  
2. Fare clic su **ID**.  
  
     L'elenco di thread viene ora ordinato in base al numero ID del thread.  
  
3. Fare clic con il pulsante destro del mouse su un thread dell'elenco. Scegliere **visualizzazione esadecimale**dal menu di scelta rapida.  
  
     Il formato dei numeri ID del thread cambia.  
  
4. Posizionare il puntatore del mouse su un thread dell'elenco.  
  
     Verrà visualizzato un suggerimento dati con uno stack di chiamate parziale per il thread.  
  
5. Osservare la quarta colonna a sinistra, denominata **Category**. I thread vengono classificati in categorie.  
  
     Il primo thread creato in un processo è denominato thread principale. Individuarlo nell'elenco di thread.  
  
6. Fare clic con il pulsante destro del mouse sul thread principale, quindi scegliere **passa a thread**.  
  
     Viene visualizzata una finestra di dialogo di avviso. in cui viene indicato che non è possibile visualizzare il codice sorgente per il thread principale in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Fare clic su **OK**.  
  
7. Esaminare la finestra **stack di chiamate** e la barra degli strumenti **posizione di debug** .  
  
     Il contenuto della finestra **stack di chiamate** è stato modificato.  
  
## <a name="switching-the-active-thread"></a>Passaggio al thread attivo  
  
#### <a name="to-switch-threads"></a>Per passare da un thread all'altro  
  
1. Nella finestra **thread** esaminare la seconda colonna da sinistra. Il pulsante all'inizio di questa colonna non presenta alcun testo o icona. Questa colonna è la colonna **thread attiva** .  
  
2. Osservare la colonna **thread attivo** e notare che un thread ha una freccia gialla. Si tratta dell' *indicatore del thread attivo*.  
  
3. Annotare il numero ID del thread dove è posizionato l'indicatore del thread attivo. Spostare l'indicatore del thread attivo in un altro thread, riportandolo però nella posizione originaria al termine dell'operazione.  
  
4. Fare clic con il pulsante destro del mouse su un altro thread, quindi scegliere **passa al thread**.  
  
5. Esaminare la finestra **stack di chiamate** nella finestra di origine. Il contenuto è cambiato.  
  
6. Esaminare la barra degli strumenti **posizione di debug** . Anche il thread attivo è cambiato.  
  
7. Passare alla barra degli strumenti **posizione di debug** . Fare clic sulla casella **thread** e scegliere un thread diverso dall'elenco a discesa.  
  
8. Esaminare la finestra **thread** . L'indicatore del thread attivo è cambiato.  
  
9. Nella finestra di origine fare nuovamente clic con il pulsante destro del mouse su un marcatore del thread. Scegliere **passa a** dal menu di scelta rapida e fare clic sul nome del thread o sul numero ID.  
  
     Sono ora disponibili tre modi per modificare il thread attivo: tramite la finestra **thread** , la casella **thread** nella barra degli strumenti **posizione di debug** e l'indicatore del thread nella finestra di origine.  
  
     Con l'indicatore del thread è possibile passare solo ai thread che sono stati interrotti in quella determinata posizione. Con la finestra **Thread** e la barra degli strumenti **Posizione di debug** è possibile passare a tutti i tipi di thread.  
  
## <a name="freezing-and-thawing-thread-execution"></a>Blocco e sblocco dell'esecuzione dei thread  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Per bloccare e sbloccare i thread  
  
1. Nella finestra **thread** fare clic con il pulsante destro del mouse su un thread, quindi scegliere **blocca**.  
  
2. Osservare la colonna dei thread attivi. Vengono visualizzate ora due barre verticali. Queste due barre blu indicano che il thread è bloccato.  
  
3. Esaminare la colonna **Suspend** . Il conteggio di sospensione per il thread ora è 1.  
  
4. Fare clic con il pulsante destro del mouse sul thread bloccato, quindi scegliere **Sblocca**.  
  
     La colonna del thread attivo e la colonna **Suspend** cambiano.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug di applicazioni multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura: passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)
