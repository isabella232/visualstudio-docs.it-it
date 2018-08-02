---
title: Eseguire il debug di un'applicazione multithreading
description: Eseguire il debug usando la finestra thread e la barra degli strumenti posizione di Debug in Visual Studio
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 65626bc483d7794c2adae141903783238a97eddd
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468465"
---
# <a name="walkthrough-debug-a-multithreaded-application-in-visual-studio-using-the-threads-window"></a>Procedura dettagliata: Debug di un'applicazione multithreading in Visual Studio usando la finestra thread
Visual Studio offre un' **thread** finestra e un'interfaccia utente gli elementi che consentono di eseguire il debug di applicazioni multithreading. Questa esercitazione illustra come usare il **thread** finestra e il **posizione di Debug** sulla barra degli strumenti. Per informazioni su altri strumenti, vedere [iniziare il debug di applicazioni multithreading](../debugger/get-started-debugging-multithreaded-apps.md). Questa esercitazione richiede solo pochi minuti, ma il suo completamento consentirà di familiarizzare con le funzionalità per il debug di applicazioni multithreading.   
  
Prima di iniziare questa esercitazione, è necessario un progetto di applicazione a thread multipli. Per creare tale progetto, attenersi alla procedura qui indicata.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Per creare il progetto di app a thread multipli  
  
1.  Nel **File** menu, scegliere **New** e quindi fare clic su **progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  Nel **tipo di progetto**s, scegliere il linguaggio di propria scelta: **Visual Basic**, **Visual c#**, oppure **Visual C++**.  
  
3.  Sotto **Desktop di Windows**, scegliere **App Console**.  
  
4.  Nel **nome** casella, digitare il nome MyThreadWalkthroughApp.  
  
5.  Fare clic su **OK**.  
  
     Verrà visualizzato un nuovo progetto console. Dopo aver creato il progetto, viene visualizzato un file di origine. A seconda del linguaggio scelto, il nome del file di origine potrebbe essere Module1.vb, Program.cs o MyThreadWalkthroughApp.cpp  
  
6.  Eliminare il codice riportato nel file di origine e sostituirlo con il codice di esempio che viene visualizzato nella sezione "Creazione di un Thread" dell'argomento [creazione di thread e passaggio di dati in fase di avvio](/dotnet/standard/threading/creating-threads-and-passing-data-at-start-time).  
  
7.  Nel **File** menu, fare clic su **Salva tutto**.  
  
#### <a name="to-begin-the-tutorial"></a>Per iniziare l'esercitazione  
  
-   Nell'editor del codice sorgente, cercare il codice seguente:  
  
    ```VB  
    Thread.Sleep(3000)   
    Console.WriteLine()
    ```  
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
  
#### <a name="to-start-debugging"></a>Per avviare il debug  
  
1.  Fare clic sul margine a sinistra del `Console.WriteLine` istruzione per inserire un nuovo punto di interruzione.  
  
     Nella barra di navigazione sul lato sinistro dell'editor del codice sorgente, viene visualizzato un cerchio rosso. che indica l'impostazione di un punto di interruzione in tale posizione.  
  
2.  Nel **Debug** menu, fare clic su **Avvia debug** (**F5**).  
  
     Viene avviato il debug e viene avviata l'esecuzione dell'applicazione che viene quindi interrotta in corrispondenza del punto di interruzione.  
  
3.  Se a questo punto la finestra dell'applicazione console ha lo stato attivo, fare clic nella finestra di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per ripristinare lo stato attivo di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Nell'editor del codice sorgente, individuare la riga che contiene il codice seguente:  
  
    ```VB  
    Thread.Sleep(5000)   
    ```  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```
  
#### <a name="to-discover-the-thread-marker"></a>Per individuare il marcatore del thread  

1.  Nella barra degli strumenti di Debug, scegliere il **Mostra thread nell'origine** pulsante ![Mostra thread nell'origine](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker"). 
  
2.  All'estrema sinistra della finestra, In questa riga, si noterà una *marcatore del thread* icona ![marcatore del Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") che due fili. Il marcatore del thread indica l'interruzione di un thread in questa posizione.  
  
3.  Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un suggerimento dati. in cui è indicato il nome e il numero ID di ciascun thread interrotto. In questo caso, l'interruzione si è verificata in un solo thread denominato `<noname>`.  

    > [!TIP]
    > Si può risultare utile per identificare i thread senza nome rinominandoli. Nella finestra thread, scegliere **rinominare** dopo il pulsante destro del mouse sul **nome** colonna nella riga di thread.
  
4.  Fare clic sul marcatore del thread per visualizzare le opzioni disponibili nel menu di scelta rapida. 
    
  
## <a name="flagging-and-unflagging-threads"></a>Impostazione e rimozione dei flag dei thread  
È possibile contrassegnare i thread che si desidera prestare particolare attenzione. Contrassegnare i thread è un buon metodo per tenere traccia dei thread importanti e per ignorare i thread che non è rilevante.  
  
#### <a name="to-flag-threads"></a>Per impostare i flag dei thread   

1.  Sul **View** dal menu **barre degli strumenti**.  
  
    Assicurarsi che il **posizione di Debug** sulla barra degli strumenti è selezionato.

2.  Andare alla **posizione di Debug** sulla barra degli strumenti e fare clic sui **Thread** elenco.  
  
    > [!NOTE]
    >  In questa barra degli strumenti sono presenti tre elenchi principali: **processo**, **Thread**, e **Stack Frame**.  
  
3.  Osservare il numero di thread visualizzati nell'elenco.  
  
4.  Tornare all'editor del codice sorgente e fare clic sul marcatore del thread ![marcatore del Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") nuovamente.  
  
5.  Nel menu di scelta rapida, scegliere **Flag**, quindi scegliere il nome del thread e il numero di ID.  
  
6.  Tornare alla **posizione di debug** sulla barra degli strumenti e trovare il **Mostra solo thread con flag** icona ![Mostra thread con flag](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker") per il a destra il **Thread** elenco.  
  
    L'icona del flag del pulsante è stato visualizzato in grigio prima. A questo punto, si tratta di un pulsante attivo.  
  
7.  Scegliere il **Mostra solo thread con flag** icona.  
  
    Nell'elenco viene visualizzato ora solo il thread con flag. (È possibile fare clic sul pulsante singolo flag per passare al **Mostra tutti i thread** modalità.)

8. Aprire la finestra thread scegliendo **Debug > Windows > thread**.

    ![Finestra thread](../debugger/media/dbg-threads-window.png "ThreadsWindow")  
  
    Nel **thread** finestra, il thread con flag dispone di un'icona del flag rossa collegato a esso.

    > [!TIP]
    > Quando si hanno alcuni thread con flag, è possibile fare doppio clic su una riga di codice nell'editor del codice e scegliere **eseguire i thread con flag fino al cursore** (assicurarsi che si sceglie di codice che tutti i thread con flag raggiungeranno). Questo verrà messo in pausa thread nella riga selezionata di codice, rendendo più semplice controllare l'ordine di esecuzione da [blocco e sblocco dei thread](#bkmk_freeze).
  
11. Nell'editor del codice sorgente, fare clic sul marcatore del thread.  
  
     Osservare ora le scelte disponibili nel menu di scelta rapida. Invece di **Flag**, sarà ora disponibile **Rimuovi flag**. Non fare clic **Rimuovi flag**.  

     Per informazioni su come rimuovere i flag dei thread, passare alla procedura successiva.  
  
#### <a name="to-unflag-threads"></a>Per rimuovere i flag dei thread  
  
1.  Nel **thread** finestra, fare doppio clic sulla riga che corrisponde al thread con flag.  
  
     Verrà visualizzato un menu di scelta rapida. Sono disponibili le opzioni **Rimuovi flag** e **Rimuovi flag di tutti i thread**.  
  
2.  Per rimuovere i flag del thread, fare clic su **Rimuovi flag**.  

    Esaminare i **posizione di debug** nuovamente sulla barra degli strumenti. Il **Mostra solo thread con flag** pulsante viene visualizzata nuovamente in grigio. È stato rimosso il flag dall'unico thread con flag. Poiché non esistono nessun thread con flag, la barra degli strumenti è tornata alla **Mostra tutti i thread** modalità. Scegliere il **Thread** elencare e verificare che è possibile visualizzare tutti i thread.  
  
5.  Tornare al **thread** finestra ed esaminare le colonne di informazioni.  
  
    Nella prima colonna, si noterà un'icona di contorno di contrassegno in ogni riga dell'elenco di thread. (Il contorno significa che il thread senza flag.)  
  
6.  Fare clic sul flag struttura icone per due thread, il secondo e terzo dalla fine dell'elenco. 

    Le icone del flag con profili vuoti vengono sostituite da icone di colore rosso.  
  
7.  Fare clic sul pulsante nella parte superiore della colonna dei flag.  
  
    Quando si fa clic su questo pulsante, cambia l'ordine dell'elenco di thread visualizzando ora i thread con flag all'inizio.  
  
8.  Fare nuovamente clic sul pulsante nella parte superiore della colonna dei flag.  
  
    L'ordine cambia di nuovo.  
  
## <a name="more-about-the-threads-window"></a>Ulteriori informazioni sulla finestra Thread  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Per ulteriori informazioni sulla finestra Thread  
  
1.  Nel **thread** finestra, esaminare la terza colonna da sinistra. Il pulsante nella parte superiore di questa colonna è **ID**.  
  
2.  Fare clic su **ID**.  
  
     L'elenco di thread viene ora ordinato in base al numero ID del thread.  
  
3.  Fare clic con il pulsante destro del mouse su un thread dell'elenco. Nel menu di scelta rapida, fare clic su **visualizzazione esadecimale**.  
  
     Il formato dei numeri ID del thread cambia.  
  
4.  Posizionare il puntatore del mouse sul **posizione** colonna per qualsiasi thread nell'elenco.  
  
     Verrà visualizzato un suggerimento dati con uno stack di chiamate parziale per il thread.

     > [!TIP]
     > Per visualizzare graficamente gli stack di chiamate per i thread, aprire il [stack in parallelo](../debugger/using-the-parallel-stacks-window.md) finestra (durante il debug, scegliere **eseguire il Debug / Windows / stack in parallelo**).  
  
5.  Osservare la quarta colonna da sinistra, contrassegnato **categoria**. I thread vengono classificati in categorie.  
  
     Il primo thread creato in un processo è denominato thread principale. Individuarlo nell'elenco di thread.  
  
6.  Fare doppio clic il thread principale e quindi fare clic su **passa al Thread**.  
  
     Oggetto **modalità interruzione** verrà visualizzata la finestra. Indica che il debugger non è attualmente in esecuzione qualsiasi codice che può visualizzare (poiché il thread principale).   
  
7.  Esaminare i **Stack di chiamate** finestra e il **posizione di Debug** sulla barra degli strumenti.  
  
     Il contenuto del **Stack di chiamate** finestra sono stati modificati. 

## <a name="bkmk_freeze"></a> Blocco e sblocco dell'esecuzione del thread 

È possibile bloccare e sbloccare (sospendere e riprendere) i thread per controllare l'ordine in cui i thread di eseguono operazioni. Ciò consente di risolvere i problemi di concorrenza, ad esempio i deadlock e race condition.

> [!TIP]
> Se si desidera seguire un solo thread senza bloccare altri thread (anche un comune scenario di debug), vedere [iniziare il debug di applicazioni multithreading](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Per bloccare e sbloccare i thread  
  
1.  Nel **thread** finestra, fare doppio clic su uno o più thread e quindi fare clic su **Freeze**.  
  
2.  Esaminare la seconda colonna (la colonna del thread corrente). L'icona di sospensione viene visualizzata ora non esiste. Tali sospendere l'icona indica che il thread è bloccato.  
  
3.  Mostra le **numero sospesi** colonna selezionandolo nel **colonne** elenco.

    Il conteggio di sospensione per il thread ora è 1.  
  
4.  Fare clic sul thread bloccato e quindi fare clic su **Sblocca**.  
  
     La colonna del thread corrente e il **conteggio sospeso** modifica della colonna. 
  
## <a name="switching-the-to-another-thread"></a>Cambio del a un altro thread 
  
#### <a name="to-switch-threads"></a>Per passare da un thread all'altro  
  
1.  Nel **thread** finestra, esaminare la seconda colonna da sinistra (la colonna del thread corrente). Il pulsante all'inizio di questa colonna non presenta alcun testo o icona.
  
2.  Esaminare la colonna del thread corrente e si noti che un thread ha una freccia gialla. La freccia gialla indica che questo thread è il thread corrente (questo è il percorso corrente del puntatore di esecuzione).
  
    Prendere nota del numero di ID di thread in cui viene visualizzata l'icona di thread corrente. Si passerà l'icona del thread corrente a un altro thread, ma è necessario inserirlo nuovamente al termine. 
  
3.  Fare doppio clic su un altro thread e quindi fare clic su **passa al Thread**.  
  
4.  Esaminare i **Stack di chiamate** finestra nell'editor del codice sorgente. Il contenuto è cambiato.  
  
5.  Esaminare i **posizione di Debug** sulla barra degli strumenti. L'icona del thread corrente è stato modificato, troppo.  
  
6.  Andare alla **posizione di Debug** sulla barra degli strumenti. Selezionare un altro thread dal **Thread** elenco.  
  
7.  Esaminare i **thread** finestra. L'icona del thread corrente è stata modificata.  
  
8. Nell'editor del codice sorgente, fare doppio clic su un marcatore del thread. Nel menu di scelta rapida, scegliere **passa al Thread** e fare clic su un numero di nome/ID thread.  
  
     Sono stati analizzati tre modi per modificare l'icona del thread corrente a un altro thread: usando il **thread** finestra, il **Thread** nell'elenco il **posizione di Debug** barra degli strumenti e il marcatore del thread nell'editor del codice sorgente.  
  
     Con il marcatore del thread, è possibile passare solo ai thread che sono stati interrotti in quella determinata posizione. Tramite il **thread** finestra e **posizione di Debug** sulla barra degli strumenti, è possibile passare a uno o più thread.   
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura: Passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)
