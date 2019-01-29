---
title: Visualizzare i thread nel debugger | Microsoft Docs
ms.date: 10/29/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9759b988e592b122866701b398eec55aedd8e95
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54228019"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window-c-visual-basic-c"></a>Visualizzare i thread nel debugger di Visual Studio usando la finestra thread (C#, Visual Basic, C++)
Nel **thread** finestra, è possibile esaminare e utilizzare i thread nell'applicazione che sta eseguendo il debug. Per istruzioni dettagliate su come usare il **thread** finestra, vedere [procedura dettagliata: Eseguire il debug usando la finestra thread](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>Usare la finestra Thread 
 Il **thread** finestra contiene una tabella in cui ogni riga descrive un thread separato nell'applicazione. Per impostazione predefinita, nella tabella sono elencati tutti i thread dell'applicazione, ma è possibile filtrare l'elenco per visualizzare solo i thread desiderati. Ogni colonna descrive un tipo di informazioni diverso. È possibile inoltre nascondere alcune colonne. Se si visualizzano tutte le colonne, vengono visualizzate le colonne seguenti, da sinistra a destra:  
  
- **Flag** In questo articolo etichetta, è possibile contrassegnare un thread a cui si desidera prestare particolare attenzione. Per informazioni su come contrassegnare un thread, vedere [come: Impostare e rimuovere i flag dei thread  
  
- -   Thread corrente In questo articolo etichetta, una freccia gialla indica che il thread corrente. Un contorno freccia indica il contesto di debug correnti per un thread non correnti.
  
- **ID**: Visualizza il numero di identificazione per ogni thread.  
  
- -   ID gestito Visualizza i numeri di identificazione gestiti per i thread gestiti.  
  
- **Categoria**. Visualizza la categoria di thread come thread dell'interfaccia utente, gestori delle chiamate a procedura remota o thread di lavoro. Una categoria speciale identifica il thread principale dell'applicazione.  
  
- **name**). Identifica ogni thread in base al nome, se presente, o come \<No Name >.  
  
- **location**: Mostra in cui il thread è in esecuzione. È possibile espandere questo percorso per visualizzare lo stack di chiamate completo per il thread.  
  
- -   Priorità Colonna avanzata (nascosta per impostazione predefinita) che consente di visualizzare la priorità o precedenza assegnata dal sistema per ogni thread.  
  
- -   Maschera di affinità Colonna avanzata (nascosta per impostazione predefinita) che mostra la maschera di affinità processori per ogni thread. In un sistema con più processori, la maschera di affinità determina in quali processori è possibile eseguire un thread.  
  
- -   Numero sospesi Colonna avanzata (nascosta per impostazione predefinita) che visualizza il numero sospesi. Questo conteggio determina se un thread può essere eseguito. Per altre informazioni sui conteggi sospesi, vedere [bloccare e sbloccare i thread](#freeze-and-thaw-threads).  
  
- -   Nome processo Colonna avanzata (nascosta per impostazione predefinita) che consente di visualizzare il processo a cui appartiene ogni thread. I dati in questa colonna possono essere utili quando si esegue il debug più processi.  

- ID processo Colonna avanzata (nascosta per impostazione predefinita) che visualizza l'ID del processo a cui appartiene ogni thread. 

- Qualificatore di trasporto Colonna avanzata (nascosta per impostazione predefinita) che identifica in modo univoco identifica il computer a cui è connesso il debugger. 
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Per visualizzare la finestra Thread in modalità di interruzione o di esecuzione  
  
-   Mentre Visual Studio è in modalità di debug, selezionare la **Debug** dal menu **Windows**, quindi selezionare **thread**.  
  
### <a name="to-display-or-hide-a-column"></a>Per visualizzare o nascondere una colonna  
  
-   Sulla barra degli strumenti in cima il **thread** finestra, seleziona **colonne**. Quindi, selezionare o deselezionare il nome della colonna che si desidera visualizzare o nascondere.  

## <a name="display-flagged-threads"></a>Visualizzare i thread con flag  
 È possibile contrassegnare un thread a cui si vuole prestare particolare attenzione mediante un'icona nella finestra **Thread**. Per altre informazioni, vedere [Procedura: Impostare e rimuovere i flag dei thread](../debugger/how-to-flag-and-unflag-threads.md). Nella finestra **Thread** è possibile scegliere di visualizzare tutti i thread o solo i thread con flag.  
  
### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag  
  
-   Scegliere **Mostra solo con flag thread** sulla barra degli strumenti in cima il **thread** finestra. (Se si è inattivo, è necessario contrassegnare alcuni thread prima di tutto.) 

## <a name="freeze-and-thaw-threads"></a>Bloccare e sbloccare i thread  
 Quando si blocca un thread, il sistema non si avvia l'esecuzione del thread anche se sono disponibili le risorse.  
  
 Nel codice nativo, è possibile sospendere o riprendere i thread chiamando le funzioni di Windows `SuspendThread` e `ResumeThread`. In alternativa, chiamare le funzioni MFC [CWinThread:: SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) e [CWinThread:: ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). Se si chiama `SuspendThread` oppure `ResumeThread`, il *numero sospesi* illustrato nel **thread** finestra verrà modificata. Il numero sospesi non cambia se si blocca o sblocca un thread nativo. Un thread non è possibile eseguire in codice nativo a meno che non sia sbloccato e presenta un numero sospesi pari a zero.  
  
 Nel codice gestito, il numero sospesi cambia quando si blocca o sblocca un thread. Se si blocca un thread in codice gestito, il numero sospesi è 1. Quando si blocca un thread in codice nativo, il numero sospesi è 0, a meno che non è stato usato il `SuspendThread` chiamare.  
  
> [!NOTE]
>  Quando si esegue il debug di una chiamata da codice nativo a codice gestito, il codice gestito viene eseguito nello stesso thread fisico del codice nativo che lo ha chiamato. Sospendendo o bloccando l'esecuzione del thread di codice nativo si otterrà anche il blocco del codice gestito.  
  
### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Per bloccare o sbloccare l'esecuzione di un thread  
  
-   Sulla barra degli strumenti nella parte superiore del **thread** finestra, seleziona **Blocca thread** oppure **Sblocca thread**.  
  
     Questa azione influisce solo sui thread selezionati nella finestra **Thread**. 

### <a name="switch-to-another-thread"></a>Passare a un altro thread 

Una freccia gialla indica il thread corrente (e la posizione del puntatore esecuzione). Una freccia verde ricurva indica che un thread non correnti è il contesto di debug corrente.

#### <a name="to-switch-to-another-thread"></a>Per passare a un altro thread  
  
-   Seguire uno dei passaggi seguenti:  
  
    -   Fare doppio clic su un thread.  
  
    -   Fare doppio clic su un thread e selezionare **Switch per Thread**.

## <a name="group-and-sort-threads"></a>Raggruppare e ordinare i thread  
 Quando si raggruppano i thread, nella tabella viene visualizzata un'intestazione per ogni gruppo. L'intestazione contiene una descrizione del gruppo, ad esempio **Thread di lavoro** o **Thread senza flag**, e un controllo albero. I thread membro di ciascuno gruppo appaiono sotto l'intestazione del gruppo. Se si desidera nascondere i thread membro di un gruppo, usare il controllo albero per comprimere il gruppo.  
  
 Poiché il raggruppamento ha la precedenza sull'ordinamento, è possibile ad esempio raggruppare i thread per categoria, per poi ordinarli in base all'ID all'interno di ogni categoria.  
  
### <a name="to-sort-threads"></a>Per ordinare i thread  
  
1.  Sulla barra degli strumenti in cima il **thread** finestra, selezionare il pulsante nella parte superiore di qualsiasi colonna.  
  
     I thread verranno ordinati in base ai valori in quella colonna.  
  
2.  Se si desidera invertire l'ordinamento, selezionare di nuovo lo stesso pulsante.  
  
     I thread che prima erano visualizzati all'inizio dell'elenco appariranno al fondo.  
  
### <a name="to-group-threads"></a>Per raggruppare i thread  
  
-   Nel **thread** degli strumenti della finestra, selezionare la **Raggruppa** elenco, quindi selezionare i criteri che si desidera raggruppare i thread.  
  
### <a name="to-sort-threads-within-groups"></a>Per ordinare i thread all'interno di gruppi  
  
1.  Sulla barra degli strumenti nella parte superiore del **thread** finestra, seleziona la **Raggruppa per** elenco, quindi selezionare i criteri che si desidera raggruppare i thread.  
  
2.  Nel **thread** finestra, selezionare il pulsante nella parte superiore di qualsiasi colonna.  
  
     I thread verranno ordinati in base ai valori in quella colonna.  
  
### <a name="to-expand-or-collapse-all-groups"></a>Per espandere o comprimere tutti i gruppi  
  
-   Sulla barra degli strumenti in cima il **thread** finestra, seleziona **espandere i gruppi** o **comprimere i gruppi**.  
  
## <a name="search-for-specific-threads"></a>Cercare thread specifici  
 È possibile cercare i thread che corrispondono a una stringa specificata nel **thread** finestra. Quando cercano i thread, la finestra Visualizza tutti i thread di corrispondenza con la stringa di ricerca in qualsiasi colonna. Le informazioni includono il percorso del thread visualizzato all'inizio dello stack di chiamate nella colonna **Percorso**. Per impostazione predefinita, lo stack di chiamate completo non viene eseguita la ricerca.  
  
### <a name="to-search-for-specific-threads"></a>Per cercare thread specifici  
  
1. Nella barra degli strumenti nella parte superiore della finestra **Thread** passare alla casella **Cerca** e:  

     - Immettere una stringa di ricerca e quindi premere **invio**.  
  
     \- oppure -  
  
     - Selezionare l'elenco a discesa accanto al **ricerca** casella e selezionare una stringa di ricerca di una ricerca precedente.  
  
2. (Facoltativo) Per includere lo stack di chiamate completo nella ricerca, selezionare **Cerca nello stack di chiamate**.   
  
## <a name="display-thread-call-stacks-and-switch-between-frames"></a>Visualizzare gli stack di thread e passare tra i frame  
In un programma multithread ogni thread dispone di un proprio stack di chiamate. La finestra **Thread** consente di visualizzare in modo pratico questi stack.

> [!TIP]
> Per una rappresentazione visiva dello stack di chiamate per ogni thread, usare il [stack in parallelo](../debugger/get-started-debugging-multithreaded-apps.md) finestra.
  
### <a name="to-view-the-call-stack-of-a-thread"></a>Per visualizzare lo stack di chiamate di un thread  
  
-   Nel **posizione** colonna, selezionare il triangolo invertito accanto al percorso del thread.  
  
     Il percorso si espanderà per visualizzare lo stack di chiamate del thread.  
  
### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Per visualizzare o comprimere gli stack di chiamate di tutti i thread  
  
-   Sulla barra degli strumenti nella parte superiore del **thread** finestra, seleziona **Espandi stack di chiamate** oppure **Comprimi stack di chiamate**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Iniziare il debug di applicazioni multithreading](../debugger/get-started-debugging-multithreaded-apps.md)