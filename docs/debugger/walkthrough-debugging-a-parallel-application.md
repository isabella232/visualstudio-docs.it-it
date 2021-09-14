---
title: Eseguire il debug di un'applicazione parallela | Microsoft Docs
description: Eseguire il debug usando le finestre Attività in parallelo e Stack paralleli in Visual Studio
ms.date: 02/14/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks walkthrough
- parallel stacks toolwindow
- parallel tasks toolwindow
- parallel applications, debugging [C++]
- debugging, parallel applications
- parallel applications, debugging [Visual Basic]
- parallel applications, debugging [C#]
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4663892ef011841ed401331009c2d8f05b63814a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627791"
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio-c-visual-basic-c"></a>Procedura dettagliata: Debug di un'applicazione parallela in Visual Studio (C#, Visual Basic, C++)

In questa procedura dettagliata viene illustrato come usare le finestre **Attività in parallelo** e **Stack in parallelo** per eseguire il debug di un'applicazione parallela. Queste finestre consentono di comprendere e verificare il comportamento in fase di esecuzione del codice che usa Task Parallel Library [(TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) o runtime di concorrenza [.](/cpp/parallel/concrt/concurrency-runtime) Nella procedura dettagliata viene fornito un esempio di codice con punti di interruzione incorporati. Una volta interrotta l'esecuzione del codice, viene illustrato come esaminarlo usando le finestre **Attività in parallelo** e **Stack in parallelo**.

 Nella procedura dettagliata vengono spiegate le seguenti attività:

- Come visualizzare gli stack di chiamate di tutti i thread in un'unica visualizzazione.

- Come visualizzare l'elenco delle istanze di `System.Threading.Tasks.Task` create nell'applicazione.

- Come visualizzare gli stack di chiamate reali delle attività anziché dei thread.

- Come passare al codice dalle finestre **Attività in parallelo** e **Stack in parallelo**.

- Come le finestre affrontano il ridimensionamento tramite il raggruppamento, lo zoom e altre funzionalità correlate.

## <a name="prerequisites"></a>Prerequisiti
 Questa procedura dettagliata presuppone **che Just My Code** abilitata (è abilitata per impostazione predefinita nelle versioni più recenti di Visual Studio). Nel menu **Strumenti** fare clic su **Opzioni**, espandere il nodo **Debug**, selezionare **Generale**, quindi **Abilita Just My Code (solo gestito)**. Se non si imposta questa funzionalità, si può comunque utilizzare la procedura dettagliata, ma è possibile che i risultati differiscano dalle illustrazioni.

## <a name="c-sample"></a>Esempio C#
 Se si utilizza l'esempio in C#, la procedura dettagliata presuppone inoltre che il codice esterno sia nascosto. Per attivare o disattivare la visualizzazione del codice esterno, fare clic con il pulsante destro del mouse sull'intestazione della tabella **Nome** nella finestra **Stack di chiamate**, quindi selezionare o deselezionare **Mostra codice esterno**. Se non si imposta questa funzionalità, si può comunque utilizzare la procedura dettagliata, ma è possibile che i risultati differiscano dalle illustrazioni.

## <a name="c-sample"></a>Esempio in C++
 Se si utilizza l'esempio in C++, è possibile ignorare i riferimenti al codice esterno contenuti in questo argomento. Il codice esterno si applica solo all'esempio in C#.

## <a name="illustrations"></a>Illustrazioni
 Le illustrazioni contenute in questo argomento sono state registrate in un computer quad core che esegue l'esempio in C#. Benché sia possibile utilizzare altre configurazioni per completare questa procedura dettagliata, le illustrazioni potrebbero differire dalle schermate visualizzate sul computer in uso.

## <a name="creating-the-sample-project"></a>Creazione del progetto di esempio
 L'esempio di codice riportato in questa procedura dettagliata è relativo a un'applicazione che non esegue alcuna operazione. L'obiettivo è semplicemente comprendere come utilizzare le finestre degli strumenti per eseguire il debug di un'applicazione parallela.

#### <a name="to-create-the-sample-project"></a>Per creare il progetto di esempio

1. Aprire Visual Studio e creare un nuovo progetto.

   ::: moniker range=">=vs-2019"

   Se la finestra iniziale non è aperta, scegliere **Finestra** > **iniziale file**.

   Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Scegliere quindi **C#**, **C++** o **Visual Basic** dall'elenco Linguaggio e quindi scegliere Windows **dall'elenco** Piattaforma.

   Dopo aver applicato il linguaggio e i filtri della piattaforma, scegliere **l'app console** per .NET Core o C++, quindi scegliere **Avanti.**

   > [!NOTE]
   > Se il modello corretto non è visualizzato, passare **a** Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Scegliere il **carico di lavoro Sviluppo multipiattaforma .NET Core** o Sviluppo desktop con **C++,** quindi **scegliere Modifica**.

   Nella finestra **Configura il nuovo progetto** digitare un nome o usare il nome predefinito nella casella Project **nome.** Scegliere quindi **Avanti o** **Crea,** a seconda dell'opzione disponibile.

   Per .NET Core scegliere il framework di destinazione consigliato (.NET Core 3.1) o .NET 5 e quindi scegliere **Crea**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Nella barra dei menu superiore scegliere **File**  >  **nuovo**  >  **Project**. Nel riquadro sinistro della finestra **di dialogo Nuovo** progetto scegliere quanto segue:

   - Per un'app C#, in **Visual C#** scegliere **Windows Desktop** e quindi nel riquadro centrale scegliere App console **(.NET Framework).**
   - Per un Visual Basic app, in **Visual Basic** scegliere **Windows Desktop** e quindi nel riquadro centrale scegliere App console **(.NET Framework).**
   - Per un'app C++, **in Visual C++** scegliere **Windows Desktop** e quindi scegliere Windows Applicazione **console**.

   Se non viene visualizzata l'app **console (.NET Core)** o, per C++, il modello di progetto **App** console, passare a Strumenti Ottieni strumenti e   >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Scegliere il **carico di lavoro Sviluppo di desktop .NET** o Sviluppo di desktop con **C++,** quindi **scegliere Modifica**.

   Digitare quindi un nome o usare il nome predefinito e fare clic su **OK.**

   Selezionare **OK**.
   ::: moniker-end

   Verrà visualizzato un nuovo progetto console. Dopo aver creato il progetto, viene visualizzato un file di origine.

1. Aprire il file di codice con estensione CPP, CS o VB nel progetto. Eliminarne il contenuto per creare un file di codice vuoto.

1. Incollare il seguente codice per il linguaggio selezionato nel file di codice vuoto.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/debugger/cs/s.cs" id="Snippet1":::
   :::code language="cpp" source="../snippets/cpp/VS_Snippets_Misc/debugger/cpp/beta2_native.cpp" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Misc/debugger/vb/module1.vb" id="Snippet1":::

1. Scegliere **Save All** (Salva tutti) dal menu **File**.

1. Nel menu **Compila** fare clic su **Ricompila soluzione**.

    Notare che vi sono quattro chiamate a `Debugger.Break` (`DebugBreak` nell'esempio C++). Pertanto, non è necessario inserire punti di interruzione; la semplice esecuzione dell'applicazione determinerà fino a quattro interruzioni nel debugger.

## <a name="using-the-parallel-stacks-window-threads-view"></a>Utilizzo della finestra Stack in parallelo: visualizzazione Thread
 Scegliere **Avvia debug** dal menu **Debug**. Attendere che venga raggiunto il primo punto di interruzione.

#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Per visualizzare lo stack di chiamate di un singolo thread

1. Scegliere **Finestre** dal menu **Debug**, quindi **Thread**. Ancorare la finestra **Thread** nella parte inferiore di Visual Studio.

2. Scegliere **Finestre** dal menu **Debug**, quindi fare clic su **Stack di chiamate**. Ancorare la finestra **Stack di chiamate** nella parte inferiore di Visual Studio.

3. Fare doppio clic su un thread nella finestra **Thread** per far sì che diventi il thread corrente. I thread correnti presentano una freccia gialla. Quando si modifica il thread corrente, il relativo stack di chiamate viene visualizzato nella finestra **Stack di chiamate**.

#### <a name="to-examine-the-parallel-stacks-window"></a>Per esaminare la finestra Stack in parallelo

1. Scegliere **Finestre** dal menu **Debug**, quindi fare clic su **Stack in parallelo**. Assicurarsi che **Thread** sia selezionata nella casella nell'angolo superiore sinistro.

     Usando la **finestra Stack paralleli** è possibile visualizzare più stack di chiamate contemporaneamente in un'unica visualizzazione. La figura seguente mostra la **finestra Stack paralleli** sopra la **finestra Stack di** chiamate.

     ![Visualizzazione thread nella finestra Stack in parallelo](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")

     Lo stack di chiamate del thread principale viene visualizzato in una casella, mentre gli stack di chiamate degli altri quattro thread sono raggruppati in un'altra casella. I quattro thread vengono raggruppati insieme in quanto i rispettivi stack frame condividono gli stessi contesti del metodo, vale a dire si trovano negli stessi metodi: `A`, `B` e `C`. Per visualizzare gli ID thread e i nomi dei thread che condividono la stessa casella, passare il mouse sulla casella con l'intestazione (**4 Thread**). Il thread corrente viene visualizzato in grassetto.

     ![Descrizione comando che mostra ID e nomi dei thread](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")

     La freccia gialla indica lo stack frame attivo del thread corrente.

     È possibile impostare i dettagli da visualizzare per gli stack frame (**Nomi moduli**, **Tipi di parametro**, **Nomi parametri**, **Valori di parametro**, **Numeri di riga** e **Offset dei byte**) facendo clic con il pulsante destro del mouse nella finestra **Stack di chiamate**.

     Un'evidenziazione blu attorno a una casella indica che il thread corrente è parte di quella casella. Il thread corrente è inoltre indicato dallo stack frame in grassetto nella descrizione comandi. Facendo doppio clic sul thread principale nella finestra Thread, si osserverà che l'evidenziazione blu nella finestra **Stack in parallelo** si sposta di conseguenza.

     ![Thread principale evidenziato nella finestra Stack in parallelo](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Per riprendere l'esecuzione fino al secondo punto di interruzione

1. Per riprendere l'esecuzione fino al raggiungimento del secondo punto di interruzione, fare clic su **Continua** nel menu **Debug**. Nell'illustrazione seguente viene mostrata la struttura ad albero del thread in corrispondenza del secondo punto di interruzione.

     ![Finestra Stack in parallelo con molti rami](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")

     In corrispondenza del primo punto di interruzione, i quattro thread erano passati tutti dal metodo S.A a S.B e a S.C. Le informazioni sono ancora visibili nella finestra **Stack in parallelo**, ma i quattro thread sono avanzati. Uno di essi ha proseguito fino a S.D, quindi a S.E. Un altro ha proseguito fino a S.F, S.G e S.H. Gli altri due hanno proseguito fino a S.I e S.J, dopo di che uno è passato a S.K mentre l'altro ha proseguito fino al codice esterno non utente.

     È possibile passare il mouse sull'intestazione della casella, ad esempio **1 thread** o **2 thread**, per visualizzare gli ID dei thread. Passando invece il mouse sugli stack frame, verranno visualizzati gli ID dei thread e altri dettagli sui frame. L'evidenziazione blu indica il thread corrente, mentre la freccia gialla indica lo stack frame attivo del thread corrente.

     L'icona dei thread di attesa (linee interweaved) indica gli stack frame attivi dei thread non ricorrenti. Fare doppio clic su S.B nella finestra **Stack di chiamate** per passare da un frame all'altro. Nella finestra **Stack in parallelo** lo stack frame corrente del thread corrente è indicato tramite un'icona con una freccia circolare verde.

     Passare da un thread all'altro nella finestra **Thread** e osservare che la visualizzazione nella finestra **Stack in parallelo** viene aggiornata.

     Per passare a un altro thread, o a un altro frame di un altro thread, è possibile usare il menu di scelta rapida nella finestra **Stack in parallelo**. Ad esempio, fare clic con il pulsante destro del mouse su S.J, scegliere **Passa a frame**, quindi fare clic su un comando.

     ![Percorso di esecuzione di stack paralleli](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")

     Fare clic con il pulsante destro del mouse su S.C e scegliere **Passa a frame**. Uno dei comandi presenta un segno di spunta che indica lo stack frame del thread corrente. È possibile passare a quel frame dello stesso thread (si sposterà soltanto la freccia verde) oppure passare all'altro thread (si sposterà anche l'evidenziazione blu). Nell'illustrazione seguente viene mostrato il sottomenu.

     ![Menu degli stack con 2 opzioni su C mentre J è corrente](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")

     Quando un contesto del metodo è associato a un unico stack frame, nell'intestazione della casella viene visualizzato **1 thread**; fare doppio clic per passare a esso. Facendo doppio clic su un contesto del metodo al quale sono associati più frame, verrà visualizzato automaticamente il menu. Passando il mouse sui contesti del metodo, notare il triangolo nero sulla destra. Il menu di scelta rapida verrà visualizzato anche facendo clic su quel triangolo.

     Nel caso di applicazioni di grandi dimensioni con molti thread, è possibile concentrarsi su un unico sottoinsieme di thread. Nella finestra **Stack in parallelo** è possibile visualizzare gli stack di chiamate per i soli thread con contrassegno. Per contrassegnare i thread, utilizzare il menu di scelta rapida o la prima cella di un thread.

     Nella barra degli strumenti fare clic sul pulsante **Mostra solo con contrassegno** accanto alla casella di riepilogo.

     ![Finestra Stack in parallelo e descrizione comando](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")

     A questo punto, nella finestra Stack in parallelo viene visualizzato solo il thread **contrassegnato.**

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Per riprendere l'esecuzione fino al terzo punto di interruzione

1. Per riprendere l'esecuzione fino al raggiungimento del terzo punto di interruzione, fare clic su **Continua** nel menu **Debug**.

     Se più thread si trovano nello stesso metodo ma questo, a sua volta, non si trovava all'inizio dello stack di chiamate, il metodo viene visualizzato in caselle diverse. Un esempio in corrispondenza del punto di interruzione corrente è S.L, il quale contiene tre thread e viene visualizzato in tre caselle. Fare doppio clic su S.L.

     ![Percorso di esecuzione nella finestra Stack in parallelo](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")

     Si noti che S.L appare in grassetto nelle altre due caselle, così da poter vedere in quali altri punti viene visualizzato. Per visualizzare quali frame chiamano in S.L e quali sono chiamati da S.L, fare clic sul pulsante **Attiva/Disattiva visualizzazione metodo** nella barra degli strumenti. La figura seguente mostra la visualizzazione del metodo della **finestra Stack in** parallelo.

     ![Visualizzazione metodo nella finestra Stack in parallelo](../debugger/media/pdb_walkthrough_4.png "PDW_Walkthrough_4")

     Si noti come il diagramma sia imperniato sul metodo selezionato e lo abbia posizionato nella propria casella al centro della visualizzazione. I chiamati e i chiamanti vengono visualizzati nella parte superiore e in quella inferiore. Fare nuovamente clic sul pulsante **Attiva/Disattiva visualizzazione metodo** per uscire da questa modalità.

     Il menu di scelta rapida della finestra **Stack in parallelo** presenta inoltre le voci descritte di seguito.

    - **Visualizzazione esadecimale** consente di scegliere tra il formato decimale e il formato esadecimale dei numeri nelle descrizioni comandi.

    - **Simbolo Impostazioni** le rispettive finestre di dialogo.

    - **Mostra thread nell'origine** attiva o disattiva la visualizzazione dei marcatori di thread nel codice sorgente, che mostra la posizione dei thread nel codice sorgente.

    - **Mostra codice esterno** consente di visualizzare tutti i frame anche se non si trovano nel codice utente. Provare questa voce per vedere il diagramma espandersi per accogliere i frame aggiuntivi, i quali possono essere disattivati in quanto non si dispone di simboli per tali frame.

2. Nella finestra **Stack in parallelo** assicurarsi che il pulsante **Scorrimento automatico a stack frame corrente** nella barra degli strumenti sia attivato.

     Quando si dispone di diagrammi di grandi dimensioni e si avanza al punto di interruzione successivo, è possibile far sì che la visualizzazione scorra automaticamente fino allo stack frame attivo del thread corrente, vale a dire il thread che per primo ha raggiunto il punto di interruzione.

3. Prima di continuare, nella finestra **Stack in parallelo** scorrere fino in fondo verso sinistra e verso il basso.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Per riprendere l'esecuzione fino al quarto punto di interruzione

1. Per riprendere l'esecuzione fino al raggiungimento del quarto punto di interruzione, fare clic su **Continua** nel menu **Debug**.

     Si noti come la visualizzazione sia scorsa automaticamente fino al punto in questione. Passare da un thread all'altro nella finestra **Thread** o da uno stack frame all'altro nella finestra **Stack di chiamate** e notare come la visualizzazione scorra sempre automaticamente al frame corretto. Disattivare l'opzione **Scorrimento automatico a stack frame corrente** e osservare la differenza.

     La **Visualizzazione panoramica** risulta utile anche con diagrammi di grandi dimensioni nella finestra **Stack in parallelo**. Per impostazione predefinita, **la visualizzazione a vista d'occhio è** impostata su On. È tuttavia possibile attivarlo o disattivarlo facendo clic sul pulsante tra le barre di scorrimento nell'angolo inferiore destro della finestra, come illustrato nella figura seguente.

     ![Visualizzazione a&#45;nella finestra Stack in parallelo](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")

     Nella visualizzazione panoramica è possibile spostare il rettangolo per eseguire rapidamente una panoramica del diagramma.

     Un altro modo per spostare il diagramma in una direzione qualsiasi è fare clic su un'area vuota del diagramma e trascinarlo nel punto desiderato.

     Per lo zoom avanti e indietro del diagramma, tenere premuto CTRL mentre si muove la rotella del mouse. In alternativa, fare clic sul pulsante Zoom nella barra degli strumenti, quindi utilizzare lo strumento Zoom.

     È anche possibile visualizzare gli stack dall'alto verso il basso, anziché dal basso verso l'alto. A tale scopo, fare clic sul menu **Strumenti**, scegliere **Opzioni**, quindi selezionare o deselezionare l'opzione nel nodo **Debug**.

2. Prima di continuare, fare clic su **Termina debug** nel menu **Debug** per terminare l'esecuzione.

## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Utilizzo della finestra Attività in parallelo e della visualizzazione Attività della finestra Stack in parallelo
 Prima di proseguire, si consiglia di completare le procedure precedenti.

#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>Per riavviare l'applicazione fino al raggiungimento del primo punto di interruzione

1. Nel menu **Debug** fare clic su **Avvia debug** e attendere il raggiungimento del primo punto di interruzione.

2. Scegliere **Finestre** dal menu **Debug**, quindi **Thread**. Ancorare la finestra **Thread** nella parte inferiore di Visual Studio.

3. Scegliere **Finestre** dal menu **Debug**, quindi **Stack di chiamate**. Ancorare **la finestra Stack** di chiamate nella parte inferiore Visual Studio.

4. Fare doppio clic su un thread nella finestra **Thread** per far sì che diventi il thread corrente. I thread correnti presentano la freccia gialla. Quando si modifica il thread corrente, le altre finestre vengono aggiornate. Si esamineranno quindi le attività.

5. Scegliere **Debug** dal menu Debug **Windows** e quindi fare clic su **Attività**. La figura seguente mostra la **finestra** Attività.

     ![Quattro attività in esecuzione nella finestra Attività](../debugger/media/pdb_walkthrough_6.png "PDW_Walkthrough_6")

     Per ogni attività in esecuzione è possibile visualizzare il relativo ID, restituito dalla proprietà omonima, l'ID e il nome del thread che la esegue e il relativo percorso (passando il mouse sul percorso viene visualizzata una descrizione comandi con l'intero stack di chiamate). Inoltre, nella colonna **Attività** è possibile visualizzare il metodo passato nell'attività, in altre parole il punto iniziale.

     Le colonne possono essere ordinate. Si noti il glifo di ordinamento che indica la colonna e la direzione di ordinamento. È anche possibile riordinare le colonne trascinandole a sinistra o a destra.

     La freccia gialla indica l'attività corrente. Per passare da un'attività all'altra, fare doppio clic su un'attività o utilizzare il menu di scelta rapida. Quando si passa da un'attività all'altra, il thread sottostante diventa quello corrente e le altre finestre vengono aggiornate.

     Quando si passa manualmente da un'attività a un'altra, la freccia gialla si sposta, ma una freccia bianca continua a mostrare l'attività che ha causato l'interruzione nel debugger.

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Per riprendere l'esecuzione fino al secondo punto di interruzione

1. Per riprendere l'esecuzione fino al raggiungimento del secondo punto di interruzione, fare clic su **Continua** nel menu **Debug**.

     In precedenza, **la** colonna Stato mostrava tutte le attività come Attive, ma ora due attività sono bloccate. Le attività possono essere bloccate [per diversi motivi.](/dotnet/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism) Passare il mouse su un'attività in attesa nella colonna **Stato** per conoscere il motivo per cui è bloccata. Ad esempio, nell'illustrazione seguente, l'attività 3 è in attesa dell'attività 4.

     ![Due attività in attesa nella finestra Attività](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")

     L'attività 4, a sua volta, è in attesa di un monitoraggio di proprietà del thread assegnato all'attività 2. Fare clic con il pulsante destro del mouse sulla riga di intestazione e scegliere **Colonne**  >  **Assegnazione thread** per visualizzare il valore di assegnazione thread per l'attività 2).

     ![Attività in attesa e descrizione comando nella finestra Attività](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")

     È possibile contrassegnare un'attività facendo clic sul flag nella prima colonna della **finestra** Attività.

     È possibile usare i contrassegni per tenere traccia delle attività tra i vari punti di interruzione nella stessa sessione di debug o per filtrare le attività i cui stack di chiamate vengono visualizzati nella finestra **Stack in parallelo**.

     Quando in precedenza è stata usata la finestra **Stack in parallelo**, sono stati visualizzati i thread dell'applicazione. Visualizzando nuovamente la finestra **Stack in parallelo**, questa volta si vedranno le attività dell'applicazione. A tale scopo, selezionare **Attività** nella casella in alto a sinistra. Nell'illustrazione che segue viene mostrata la visualizzazione Attività.

     ![Visualizzazione attività nella finestra Stack in parallelo](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")

     I thread che al momento non eseguono attività non vengono mostrati nella visualizzazione Attività della finestra **Stack in parallelo**. Inoltre, per i thread che eseguono attività, alcuni stack frame che non sono importanti per le attività vengono filtrati dalla parte superiore e dalla parte inferiore dello stack.

     Visualizzare di **nuovo la finestra** Attività. Fare clic con il pulsante destro del mouse su un'intestazione di colonna qualsiasi per visualizzare un menu di scelta rapida per la colonna.

     Il menu di scelta rapida può essere utilizzato per aggiungere o rimuovere colonne. Ad esempio, la colonna AppDomain non è selezionata, pertanto non viene visualizzata nell'elenco. Fare clic su **Padre**. Verrà visualizzata la colonna **Padre** senza valori per le quattro attività.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Per riprendere l'esecuzione fino al terzo punto di interruzione

1. Per riprendere l'esecuzione fino al raggiungimento del terzo punto di interruzione, fare clic su **Continua** nel menu **Debug**.

     Una nuova attività, l'attività 5, è ora in esecuzione mentre l'attività 4 è in attesa. Per visualizzare il motivo, passare il mouse sull'attività in attesa nella finestra **Stato**. Nella colonna **Padre** si noti che l'attività 4 è l'elemento padre dell'attività 5.

     Per visualizzare meglio la relazione padre-figlio, fare clic con il pulsante destro del mouse sulla riga dell'intestazione di colonna e quindi scegliere **Visualizzazione padre-figlio**. Si dovrebbe vedere l'illustrazione seguente.

     ![Visualizzazione padre&#45;figlio nella finestra Attività](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")

     Si noti che l'attività 4 e l'attività 5 sono in esecuzione nello stesso thread (visualizzare la **colonna Assegnazione** thread se è nascosta). Queste informazioni non vengono visualizzate nella **finestra Thread.** La visualizzazione qui è un altro vantaggio della **finestra** Attività. Per conferma, visualizzare la finestra **Stack in parallelo**. Assicurarsi di essere nella visualizzazione **Attività**. Individuare le attività 4 e 5 facendo doppio clic su di esse nella **finestra** Attività. L'evidenziazione blu nella finestra **Stack in parallelo** verrà di conseguenza aggiornata. È anche possibile individuare le attività 4 e 5 analizzando le descrizioni comandi nella finestra **Stack in parallelo**.

     ![Visualizzazione attività nella finestra Stack in parallelo](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")

     Fare clic con il pulsante destro del mouse su S.P nella finestra **Stack in parallelo**, quindi scegliere **Passa a thread**. La finestra passerà alla visualizzazione Thread e verrà visualizzato il thread corrispondente. È possibile vedere entrambe le attività nello stesso thread.

     ![Thread evidenziato nella visualizzazione thread](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")

     Questo è un altro vantaggio della visualizzazione Attività nella finestra **Stack in parallelo** rispetto alla finestra **Thread**.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Per riprendere l'esecuzione fino al quarto punto di interruzione

1. Per riprendere l'esecuzione fino al raggiungimento del terzo punto di interruzione, fare clic su **Continua** nel menu **Debug**. Fare clic sull'intestazione di colonna **ID** per ordinare in base all'ID. Si dovrebbe vedere l'illustrazione seguente.

     ![Quattro stati di attività nella finestra Attività in parallelo](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")

     Essendo stata completata, l'attività 5 non viene più visualizzata. Se questo non è il caso nel computer e il deadlock non viene visualizzato, eseguire un passaggio una sola volta premendo **F11.**

     L'attività 3 e l'attività 4 sono ora in attesa l'una sull'altra e sono bloccate. Vi sono inoltre 5 nuove attività che sono attività figlio dell'attività 2 e vengono ora pianificate. Le attività pianificate sono attività avviate nel codice ma non ancora eseguite. Le relative colonne **Percorso** e **Assegnazione thread** sono pertanto vuote.

     Visualizzare nuovamente la finestra **Stack in parallelo**. L'intestazione di ogni casella presenta una descrizione comandi nella quale sono visualizzati gli ID e i nomi dei thread. Passare alla visualizzazione Attività nella finestra **Stack in parallelo**. Passare il mouse su un'intestazione per visualizzare l'ID, il nome e lo stato dell'attività come mostrato nell'illustrazione seguente.

     ![Descrizione comando dell'intestazione nella finestra Stack in parallelo](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")

     È possibile raggruppare le attività in base alle colonne. Nella finestra **Attività fare** clic con il pulsante destro del mouse sull'intestazione di colonna **Stato** e quindi scegliere Raggruppa **per stato**. La figura seguente mostra la **finestra** Attività raggruppata in base allo stato.

     ![Attività raggruppate nella finestra Attività](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")

     È anche possibile raggruppare in base alle altre colonne. Raggruppando le attività, è possibile concentrarsi su un subset di attività. Ogni gruppo comprimibile presenta un conteggio degli elementi raggruppati insieme.

     L'ultima funzionalità della finestra **Attività** da esaminare è il menu di scelta rapida visualizzato quando si fa clic con il pulsante destro del mouse su un'attività.

     Il menu di scelta rapida visualizza comandi diversi a seconda dello stato dell'attività. I comandi possono includere **Copia**, **Seleziona tutto**, **Visualizzazione esadecimale**, **Passa ad attività**, **Blocca thread assegnato**, **Blocca tutti i thread ad eccezione di quello corrente**, **Sblocca thread assegnato** e **Contrassegna**.

     È possibile bloccare il thread sottostante di un'attività o di più attività oppure bloccare tutti i thread a eccezione di quello assegnato. Un thread bloccato è rappresentato nella **finestra** Attività così come nella finestra **Thread,** da un'icona di *sospensione* blu.

## <a name="summary"></a>Riepilogo
 In questa procedura dettagliata sono state illustrate le finestre del debugger **Attività in parallelo** e **Stack in parallelo**. Utilizzare queste finestre con progetti reali che a loro volta utilizzano codice multithreading. È possibile esaminare codice parallelo scritto in C++, C# o Visual Basic.

## <a name="see-also"></a>Vedi anche
- [Debug di applicazioni multithreading](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
- [Programmazione parallela](/dotnet/standard/parallel-programming/index)
- [Runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime)
- [Utilizzo della finestra Stack in parallelo](../debugger/using-the-parallel-stacks-window.md)
- [Utilizzo della finestra Attività](../debugger/using-the-tasks-window.md)
