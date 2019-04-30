---
title: "Procedura dettagliata: Debug di un'applicazione multithreading | Microsoft Docs"
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
ms.openlocfilehash: 7d598cc245421aafb05cbf91fe2b7a95e39564a2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444329"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>Procedura dettagliata: Debug di un'applicazione multithreading
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] fornisce un miglioramento **thread** finestra e un'interfaccia utente miglioramenti per renderne più semplice eseguire il debug di applicazioni multithreading. Il completamento di questa procedura dettagliata richiede solo alcuni minuti, ma è utile per familiarizzare con le nuove funzionalità dell'interfaccia per il debug delle applicazioni multithreading.  
  
 Per iniziare questa procedura dettagliata, è necessario un progetto di applicazione multithreading. Per creare tale progetto, attenersi alla procedura qui indicata.  
  
#### <a name="to-create-the-walkthrough-project"></a>Per creare il progetto necessario per la procedura dettagliata  
  
1. Nel **File** menu, scegliere **New** e quindi fare clic su **progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2. Nel **tipo di progetto**s, scegliere il linguaggio di propria scelta: **Visual Basic**, **Visual C#** , o **Visual C++**.  
  
3. Nel **modelli** , scegliere **applicazione Console** oppure **applicazione Console CLR**.  
  
4. Nel **nome** casella, digitare il nome MyThreadWalkthroughApp.  
  
5. Fare clic su **OK**.  
  
     Verrà visualizzato un nuovo progetto console. Dopo aver creato il progetto, viene visualizzato un file di origine. A seconda del linguaggio scelto, il nome del file di origine potrebbe essere Module1.vb, Program.cs o MyThreadWalkthroughApp.cpp  
  
6. Eliminare il codice riportato nel file di origine e sostituirlo con il codice di esempio che viene visualizzato nella sezione "Creazione di un Thread" dell'argomento [creazione di thread e passaggio di dati in fase di avvio](http://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d).  
  
7. Nel menu **File** fare clic su **Salva tutto**.  
  
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
  
1. Fare doppio clic il `Console.WriteLine` istruzione, scegliere **punto di interruzione** e quindi fare clic su **Inserisci punto di interruzione**.  
  
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
  
1. Fare doppio clic nella **thread** finestra, quindi fare clic su **Mostra thread nell'origine**.  
  
2. All'estrema sinistra della finestra, in corrispondenza di questa riga, verrà visualizzata un'icona con due fili, uno rosso e uno blu. Il marcatore del thread indica l'interruzione di un thread in questa posizione. È possibile, pertanto, che un thread venga interrotto in questa posizione.  
  
3. Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un suggerimento dati in cui è indicato il nome e il numero ID di ciascun thread interrotto. In questo caso, l'interruzione si è verificata in un solo thread denominato `<noname>`.  
  
4. Fare clic con il pulsante destro del mouse sul marcatore del thread per visualizzare un menu di scelta rapida.  
  
   Questa icona è un *marcatore del thread*:  
  
   ![Thread Marker](../debugger/media/threadmarker.gif "ThreadMarker")  
  
## <a name="flagging-and-unflagging-threads"></a>Impostazione e rimozione dei flag dei thread  
 In [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] è possibile impostare i flag dei thread a cui si desidera attribuire particolare attenzione. L'impostazione dei flag dei thread è un ottimo strumento per tenere traccia dei thread importanti e per ignorare quelli a cui non si desidera prestare attenzione.  
  
#### <a name="to-flag-threads"></a>Per impostare i flag dei thread  
  
1. Sul **View** dal menu **barre degli strumenti**.  
  
     Assicurarsi che il **posizione di Debug** sulla barra degli strumenti è selezionato.  
  
2. Andare alla **posizione di debug** sulla barra degli strumenti e fare clic sui **Thread** elenco.  
  
    > [!NOTE]
    > In questa barra degli strumenti sono presenti tre elenchi principali: **Processo**, **Thread**, e **Stack Frame**.  
  
3. Osservare il numero di thread visualizzati nell'elenco.  
  
4. Tornare alla finestra di origine e rapida la **Thread** marcatore nuovamente.  
  
5. Nel menu di scelta rapida, scegliere **Flag**, quindi scegliere il nome del thread e il numero di ID.  
  
6. Tornare alla **posizione di debug** sulla barra degli strumenti e fare clic sui **Thread** elencare di nuovo.  
  
     Nell'elenco viene visualizzato ora solo il thread con flag. Il pulsante del flag che si trova a destra del **Thread** elenco. L'icona del flag sul pulsante che prima era visualizzata in grigio è ora di colore rosso.  
  
7. Posizionare il puntatore del mouse sull'icona del flag.  
  
     Viene visualizzato un popup Questo popup indica la modalità di **Thread** dell'elenco è: **Mostra solo thread con flag**.  
  
8. Scegliere il pulsante del flag per visualizzare nuovamente **Mostra tutti i thread** modalità.  
  
9. Fare clic sui **Thread** elencare nuovamente e verificare che è ora possibile visualizzare tutti i thread nuovamente.  
  
10. Scegliere il pulsante del flag per visualizzare nuovamente **Mostra solo thread con flag**.  
  
11. Scegliere **Finestre** dal menu **Debug**, quindi **Thread**.  
  
     Il **thread** verrà visualizzata la finestra. in cui è presente un thread con un'icona del flag associata.  
  
12. Nella finestra di origine fare nuovamente clic con il pulsante destro del mouse sul marcatore del thread.  
  
     Osservare ora le scelte disponibili nel menu di scelta rapida. Invece di **Flag**, sarà ora disponibile **Rimuovi flag**. Non fare clic **Rimuovi flag**.  
  
13. Passare alla procedura successiva in cui viene descritto come rimuovere i flag dei thread.  
  
#### <a name="to-unflag-threads"></a>Per rimuovere i flag dei thread  
  
1. Nel **thread** finestra, fare doppio clic sulla riga che corrisponde al thread con flag.  
  
     Verrà visualizzato un menu di scelta rapida. Sono disponibili le opzioni **Rimuovi flag** e **rimuovere il flag tutti**.  
  
2. Per rimuovere i flag del thread, fare clic su **Rimuovi flag**.  
  
3. Fare clic sull'icona del flag rossa.  
  
4. Esaminare i **posizione di debug** nuovamente sulla barra degli strumenti. Il pulsante del flag è nuovamente in grigio. È stato rimosso il flag dall'unico thread con flag. Poiché non esistono nessun thread con flag, la barra degli strumenti è tornata alla **Mostra tutti i thread** modalità. Scegliere il **Thread** elencare e verificare che è possibile visualizzare tutti i thread.  
  
5. Tornare al **thread** finestra ed esaminare le colonne di informazioni.  
  
     La maggior parte dei pulsanti situati all'inizio di ogni colonna dispone di titoli che identificano la colonna. Nella prima colonna a sinistra però non è presente alcun titolo, bensì un'icona con il profilo di una bandiera. Si noterà lo stesso profilo in ogni riga dell'elenco di thread. Il profilo indica la rimozione del flag del thread.  
  
6. Fare clic sui profili di due thread, il secondo e terzo dalla fine dell'elenco.  
  
     Le icone del flag con profili vuoti vengono sostituite da icone di colore rosso.  
  
7. Fare clic sul pulsante nella parte superiore della colonna dei flag.  
  
     Quando si fa clic su questo pulsante, cambia l'ordine dell'elenco di thread visualizzando ora i thread con flag all'inizio.  
  
8. Fare nuovamente clic sul pulsante nella parte superiore della colonna dei flag.  
  
     L'ordine cambia di nuovo.  
  
## <a name="more-about-the-threads-window"></a>Ulteriori informazioni sulla finestra Thread  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Per ulteriori informazioni sulla finestra Thread  
  
1. Nel **thread** finestra, esaminare la terza colonna da sinistra. Il pulsante nella parte superiore di questa colonna è **ID**.  
  
2. Fare clic su **ID**.  
  
     L'elenco di thread viene ora ordinato in base al numero ID del thread.  
  
3. Fare clic con il pulsante destro del mouse su un thread dell'elenco. Nel menu di scelta rapida, fare clic su **visualizzazione esadecimale**.  
  
     Il formato dei numeri ID del thread cambia.  
  
4. Posizionare il puntatore del mouse su un thread dell'elenco.  
  
     Verrà visualizzato un suggerimento dati con uno stack di chiamate parziale per il thread.  
  
5. Osservare la quarta colonna da sinistra, contrassegnato **categoria**. I thread vengono classificati in categorie.  
  
     Il primo thread creato in un processo è denominato thread principale. Individuarlo nell'elenco di thread.  
  
6. Fare doppio clic il thread principale e quindi fare clic su **passa al Thread**.  
  
     Verrà visualizzata una finestra di dialogo di avviso in cui viene indicato che non è possibile visualizzare il codice sorgente per il thread principale in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Fare clic su **OK**.  
  
7. Esaminare i **Stack di chiamate** finestra e il **posizione di Debug** sulla barra degli strumenti.  
  
     Il contenuto del **Stack di chiamate** finestra sono stati modificati.  
  
## <a name="switching-the-active-thread"></a>Passaggio al thread attivo  
  
#### <a name="to-switch-threads"></a>Per passare da un thread all'altro  
  
1. Nel **thread** finestra, esaminare la seconda colonna da sinistra. Il pulsante all'inizio di questa colonna non presenta alcun testo o icona. Questa colonna è il **Thread attivo** colonna.  
  
2. Esaminare i **Thread attivo** colonna e notare che tale thread ha una freccia gialla. Questo è il *indicatore del thread attivo*.  
  
3. Annotare il numero ID del thread dove è posizionato l'indicatore del thread attivo. Spostare l'indicatore del thread attivo in un altro thread, riportandolo però nella posizione originaria al termine dell'operazione.  
  
4. Fare doppio clic su un altro thread e quindi fare clic su **passa al Thread**.  
  
5. Esaminare i **Stack di chiamate** finestra nella finestra di origine. Il contenuto è cambiato.  
  
6. Esaminare i **posizione di Debug** sulla barra degli strumenti. Anche il thread attivo è cambiato.  
  
7. Andare alla **posizione di Debug** sulla barra degli strumenti. Scegliere il **Thread** casella e scegliere un altro thread nell'elenco a discesa.  
  
8. Esaminare i **thread** finestra. L'indicatore del thread attivo è cambiato.  
  
9. Nella finestra di origine fare nuovamente clic con il pulsante destro del mouse su un marcatore del thread. Nel menu di scelta rapida, scegliere **passare a** e fare clic su un numero di nome/ID thread.  
  
     Sono stati analizzati tre modi di modifica del thread attivo: usando il **thread** finestra, il **Thread** nella casella il **posizione di Debug** sulla barra degli strumenti e l'indicatore del thread nel finestra di origine.  
  
     Con l'indicatore del thread è possibile passare solo ai thread che sono stati interrotti in quella determinata posizione. Con la finestra **Thread** e la barra degli strumenti **Posizione di debug** è possibile passare a tutti i tipi di thread.  
  
## <a name="freezing-and-thawing-thread-execution"></a>Blocco e sblocco dell'esecuzione dei thread  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Per bloccare e sbloccare i thread  
  
1. Nel **thread** finestra, fare doppio clic su uno o più thread e quindi fare clic su **Freeze**.  
  
2. Osservare la colonna dei thread attivi. Vengono visualizzate ora due barre verticali. Queste due barre blu indicano che il thread è bloccato.  
  
3. Esaminare i **Suspend** colonna. Il conteggio di sospensione per il thread ora è 1.  
  
4. Fare clic sul thread bloccato e quindi fare clic su **Sblocca**.  
  
     La colonna del thread attivo e il **Suspend** modifica della colonna.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura: Passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)
