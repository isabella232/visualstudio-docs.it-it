---
title: Visualizzare i thread nel debugger | Microsoft Docs
description: Usare i thread per esaminare e controllare i thread. È possibile raggruppare, ordinare, contrassegnare, bloccare, scongelare e cercare i thread, selezionare le colonne e visualizzare gli stack di chiamate.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cd11e722886b77e9faaace768cc30a74c759903f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884208"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window-c-visual-basic-c"></a>Visualizzare i thread nel debugger di Visual Studio tramite la finestra thread (C#, Visual Basic, C++)
Nella finestra **thread** è possibile esaminare e utilizzare i thread nell'applicazione di cui si sta eseguendo il debug. Per istruzioni dettagliate su come usare la finestra **thread** , vedere [procedura dettagliata: eseguire il debug usando la finestra thread](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>Usare la finestra Thread
 La finestra **thread** contiene una tabella in cui ogni riga descrive un thread separato nell'applicazione. Per impostazione predefinita, nella tabella sono elencati tutti i thread dell'applicazione, ma è possibile filtrare l'elenco per visualizzare solo i thread desiderati. Ogni colonna descrive un tipo diverso di informazioni. È possibile inoltre nascondere alcune colonne. Se vengono visualizzate tutte le colonne, vengono visualizzate le colonne seguenti, da sinistra a destra:

- **Flag**: in questa colonna senza etichetta è possibile contrassegnare un thread al quale si desidera prestare particolare attenzione. Per informazioni su come contrassegnare un thread, vedere [procedura: Flag e rimuovere i flag dei thread](../debugger/how-to-flag-and-unflag-threads.md).

- **Thread corrente**: In questo articolo etichetta, una freccia gialla indica che il thread corrente. Una struttura a freccia indica il contesto del debugger corrente per un thread non corrente.

- **ID**: Visualizza il numero di identificazione per ogni thread.

- **ID gestito**: visualizza i numeri di identificazione gestiti per i thread gestiti.

- **Category**: Visualizza la categoria dei thread come thread dell'interfaccia utente, gestori delle chiamate RPC o thread di lavoro. Una categoria speciale identifica il thread principale dell'applicazione.

- **Nome**: identifica ogni thread in base al nome, se ne è presente uno o come \<No Name> .

- **Location**: indica il punto in cui il thread è in esecuzione. È possibile espandere questo percorso per visualizzare lo stack di chiamate completo per il thread.

- **Priorità**: colonna avanzata (nascosta per impostazione predefinita) che consente di visualizzare la priorità o precedenza assegnata dal sistema per ogni thread.

- **Maschera di affinità**: colonna avanzata (nascosta per impostazione predefinita) che mostra la maschera di affinità processori per ogni thread. In un sistema con più processori, la maschera di affinità determina in quali processori è possibile eseguire un thread.

- **Numero sospesi**: colonna avanzata (nascosta per impostazione predefinita) che visualizza il numero sospesi. Questo conteggio determina se un thread può essere eseguito. Per altre informazioni sui conteggi sospesi, vedere [bloccare e sbloccare i thread](#freeze-and-thaw-threads).

- **Il nome del processo**: colonna avanzata (nascosta per impostazione predefinita) che consente di visualizzare il processo a cui appartiene ogni thread. I dati in questa colonna possono essere utili quando si esegue il debug di molti processi.

- **ID del processo**: ID di colonna avanzata (nascosta per impostazione predefinita) consente di visualizzare il processo a cui appartiene ogni thread.

- **Qualificatore di trasporto**: colonna avanzata (nascosta per impostazione predefinita) che identifica in modo univoco il computer a cui è connesso il debugger.

### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Per visualizzare la finestra Thread in modalità di interruzione o di esecuzione

- Mentre Visual Studio è in modalità di debug, selezionare il menu **debug** , scegliere **finestre**, quindi selezionare **thread**.

### <a name="to-display-or-hide-a-column"></a>Per visualizzare o nascondere una colonna

- Nella barra degli strumenti nella parte superiore della finestra **thread** selezionare **colonne**. Selezionare o deselezionare il nome della colonna che si desidera visualizzare o nascondere.

## <a name="display-flagged-threads"></a>Visualizza thread contrassegnati
 È possibile contrassegnare un thread a cui si vuole prestare particolare attenzione mediante un'icona nella finestra **Thread**. Per altre informazioni, vedere [procedura: contrassegnare e non contrassegnare i thread](../debugger/how-to-flag-and-unflag-threads.md). Nella finestra **Thread** è possibile scegliere di visualizzare tutti i thread o solo i thread con flag.

### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag

- Scegliere **Mostra thread con flag solo** sulla barra degli strumenti nella parte superiore della finestra **thread** . Se è disattivato, è necessario contrassegnare prima alcuni thread.

## <a name="freeze-and-thaw-threads"></a>Blocca e Sblocca thread
 Quando si blocca un thread, il sistema non avvia l'esecuzione del thread anche se le risorse sono disponibili.

 Nel codice nativo è possibile sospendere o riprendere i thread chiamando le funzioni di Windows `SuspendThread` e `ResumeThread` . In alternativa, chiamare le funzioni MFC [CWinThread:: SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) e [CWinThread:: ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). Se si chiama `SuspendThread` o `ResumeThread` , il *numero sospeso* visualizzato nella finestra **thread** verrà modificato. Il numero sospeso non cambia se si blocca o sblocca un thread nativo. Un thread non può essere eseguito nel codice nativo a meno che non venga sbloccato e abbia un conteggio sospeso pari a zero.

 Nel codice gestito, il numero sospeso cambia quando si blocca o sblocca un thread. Se si blocca un thread nel codice gestito, il numero sospeso è 1. Quando si blocca un thread in codice nativo, il numero sospeso è 0, a meno che non sia stata usata la `SuspendThread` chiamata.

> [!NOTE]
> Quando si esegue il debug di una chiamata da codice nativo a codice gestito, il codice gestito viene eseguito nello stesso thread fisico del codice nativo che lo ha chiamato. Sospendendo o bloccando l'esecuzione del thread di codice nativo si otterrà anche il blocco del codice gestito.

### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Per bloccare o sbloccare l'esecuzione di un thread

- Nella barra degli strumenti nella parte superiore della finestra **thread** selezionare **blocca thread** o **Sblocca thread**.

     Questa azione influisce solo sui thread selezionati nella finestra **Thread**.

### <a name="switch-to-another-thread"></a>Passa a un altro thread

Una freccia gialla indica il thread corrente (e la posizione del puntatore di esecuzione). Una freccia verde con una coda riccia indica che un thread non corrente ha il contesto del debugger corrente.

#### <a name="to-switch-to-another-thread"></a>Per passare a un altro thread

- Seguire una delle procedure seguenti:

  - Fare doppio clic su un thread.

  - Fare clic con il pulsante destro del mouse su un thread e selezionare **passa a thread**.

## <a name="group-and-sort-threads"></a>Raggruppare e ordinare i thread
 Quando si raggruppano i thread, nella tabella viene visualizzata un'intestazione per ogni gruppo. L'intestazione contiene una descrizione del gruppo, ad esempio **Thread di lavoro** o **Thread senza flag**, e un controllo albero. I thread membro di ciascuno gruppo appaiono sotto l'intestazione del gruppo. Se si desidera nascondere i thread del membro per un gruppo, utilizzare il controllo albero per comprimere il gruppo.

 Poiché il raggruppamento ha la precedenza sull'ordinamento, è possibile ad esempio raggruppare i thread per categoria, per poi ordinarli in base all'ID all'interno di ogni categoria.

### <a name="to-sort-threads"></a>Per ordinare i thread

1. Nella barra degli strumenti nella parte superiore della finestra **thread** selezionare il pulsante nella parte superiore di qualsiasi colonna.

     I thread verranno ordinati in base ai valori in quella colonna.

2. Se si vuole invertire l'ordinamento, selezionare di nuovo lo stesso pulsante.

     I thread che prima erano visualizzati all'inizio dell'elenco appariranno al fondo.

### <a name="to-group-threads"></a>Per raggruppare i thread

- Nella barra degli strumenti della finestra **thread** selezionare l'elenco **Raggruppa per** , quindi selezionare i criteri per i quali si desidera raggruppare i thread.

### <a name="to-sort-threads-within-groups"></a>Per ordinare i thread all'interno di gruppi

1. Nella barra degli strumenti nella parte superiore della finestra **thread** selezionare l'elenco **Raggruppa per** , quindi selezionare i criteri per i quali si desidera raggruppare i thread.

2. Nella finestra **thread** selezionare il pulsante nella parte superiore di qualsiasi colonna.

     I thread verranno ordinati in base ai valori in quella colonna.

### <a name="to-expand-or-collapse-all-groups"></a>Per espandere o comprimere tutti i gruppi

- Nella barra degli strumenti nella parte superiore della finestra **thread** selezionare **Espandi gruppi** o **Comprimi gruppi**.

## <a name="search-for-specific-threads"></a>Cerca thread specifici
 È possibile cercare i thread che corrispondono a una stringa specificata nella finestra **thread** . Quando si esegue la ricerca di thread, nella finestra vengono visualizzati tutti i thread corrispondenti alla stringa di ricerca in qualsiasi colonna. Le informazioni includono il percorso del thread visualizzato all'inizio dello stack di chiamate nella colonna **Percorso**. Per impostazione predefinita, lo stack di chiamate completo non viene cercato.

### <a name="to-search-for-specific-threads"></a>Per cercare thread specifici

1. Nella barra degli strumenti nella parte superiore della finestra **Thread** passare alla casella **Cerca** e:

     - Immettere una stringa di ricerca e premere **invio**.

     \- - oppure -

     - Selezionare l'elenco a discesa accanto alla casella di **ricerca** e selezionare una stringa di ricerca da una ricerca precedente.

2. (Facoltativo) Per includere lo stack di chiamate completo nella ricerca, selezionare **Cerca nello stack di chiamate**.

## <a name="display-thread-call-stacks-and-switch-between-frames"></a>Visualizzare gli stack di chiamate del thread e spostarsi tra i frame
In un programma multithread ogni thread dispone di un proprio stack di chiamate. La finestra **Thread** consente di visualizzare in modo pratico questi stack.

> [!TIP]
> Per una rappresentazione visiva dello stack di chiamate per ogni thread, usare la finestra [stack in parallelo](../debugger/get-started-debugging-multithreaded-apps.md) .

### <a name="to-view-the-call-stack-of-a-thread"></a>Per visualizzare lo stack di chiamate di un thread

- Nella colonna **percorso** selezionare il triangolo invertito accanto al percorso del thread.

     Il percorso si espanderà per visualizzare lo stack di chiamate del thread.

### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Per visualizzare o comprimere gli stack di chiamate di tutti i thread

- Nella barra degli strumenti nella parte superiore della finestra **thread** selezionare **Espandi stack di chiamate** o **Comprimi stack di chiamate**.

## <a name="see-also"></a>Vedi anche
- [Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Iniziare il debug di applicazioni multithreading](../debugger/get-started-debugging-multithreaded-apps.md)
