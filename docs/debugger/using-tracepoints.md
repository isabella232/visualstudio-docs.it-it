---
title: Usare punti nel debugger | Microsoft Docs
ms.date: 9/17/2019
ms.topic: conceptual
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 263657213f1720eaca7a0462bb31585adaacf9bb
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72516400"
---
# <a name="use-tracepoints-in-the-visual-studio-debugger"></a>Usare punti nel debugger di Visual Studio

Punti consentono di registrare le informazioni nella finestra di output in condizioni configurabili senza modificare o arrestare il codice. Questa funzionalità è supportata sia per il codice gestito che per quello nativo, nonché per diversi linguaggi, C#ad esempio JavaScript e.

## <a name="let39s-take-an-example"></a>Diamo&#39;un esempio

Il programma di esempio seguente è un semplice ciclo di `for` con una variabile contatore che aumenta di uno ogni volta che il ciclo esegue un'altra iterazione.

![Esempio di contatore](../debugger/media/counterexample.png "Esempio di contatore")

## <a name="set-tracepoints-in-source-code"></a>Imposta punti nel codice sorgente

È possibile impostare punti specificando una stringa di output nella casella di controllo **azione** nella finestra impostazioni del punto di **interruzione** .

1. Per inizializzare un punto di analisi, fare prima clic sulla barra a sinistra del numero di riga in cui si vuole impostare il punto di analisi.

   ![Inizializzazione del punto di interruzione](../debugger/media/breakpointinitialization.png "Inizializzazione del punto di interruzione")

2. Passare il puntatore sul cerchio rosso, quindi fare clic sull'icona a forma di ingranaggio.
3. Verrà visualizzata la finestra impostazioni del punto di **interruzione** .

   ![Finestra punto di interruzione](../debugger/media/breakpointwindow.png "Finestra punto di interruzione")

4. Selezionare la casella di controllo **azione** .

   ![Casella azioni selezionate](../debugger/media/checkedactionsbox.png "Casella azioni selezionate")

   Si noti come il cerchio rosso venga modificato in un rombo che indica che è stato passato da un punto di interruzione a un punto di analisi.

5. Immettere il messaggio per cui si vuole accedere alla casella di testo **Mostra un messaggio nella finestra di output** . per informazioni dettagliate, vedere le sezioni successive di questo articolo.

   Il punto di analisi è ora impostato. Fare clic sul pulsante &quot;Close &quot; se si desidera eseguire la registrazione di alcune informazioni all'Finestra di output.

6. Se si desidera aggiungere condizioni che determinano se il messaggio è visualizzato, selezionare la casella di controllo **condizioni** .

   ![Casella condizioni controllate](../debugger/media/checkedconditionsbox.png "Casella condizioni controllate")

   Sono disponibili tre opzioni per le condizioni: **espressione condizionale**, **filtro**e **numero di passaggi**.

## <a name="actions-menu"></a>Menu azioni

Questo menu consente di registrare un messaggio nella finestra di output. Digitare le stringhe che si desidera visualizzare nella finestra di messaggio (non sono necessarie virgolette). Se si desidera visualizzare i valori delle variabili, assicurarsi di racchiuderlo tra parentesi graffe.

Se, ad esempio, si desidera visualizzare il valore della variabile `counter` nella console di output, digitare {Counter} nella casella di testo del messaggio.

![Messaggio di output del contatore](../debugger/media/counteroutputmessage.png "Messaggio di output del contatore")

Se si fa clic su **Chiudi** e quindi si esegue il debug del programma (**F5**), nella finestra di output verrà visualizzato il seguente output.

![Messaggio azioni nella Finestra di output](../debugger/media/actionsmessageinoutputwindow.png "Messaggio azioni nella Finestra di output")

È anche possibile usare parole chiave speciali per visualizzare informazioni più specifiche. Immettere la parola chiave esattamente come mostrato di seguito (usare "$" davanti a ogni parola chiave e tutte le maiuscole per la parola chiave).

| Parola chiave | Elementi visualizzati |
| --- | --- |
| $ADDRESS | Istruzione corrente |
| $CALLER | Scegliere il nome della funzione |
| $CALLSTACK | Stack di chiamate |
| $FUNCTION | Nome della funzione corrente |
| $PID | ID processo |
| $PNAME | Nome processo |
| $TID | ID thread |
| $TNAME   | Nome thread |
| $TICK | Conteggio dei cicli (da Windows GetTickCount) |

## <a name="conditions-menu"></a>Menu condizioni

Le condizioni consentono di filtrare i messaggi di output, in modo che vengano visualizzati solo in determinati scenari. Esistono tre tipi principali di condizioni disponibili.

### <a name="conditional-expression"></a>Espressione condizionale
Per un'espressione condizionale, un messaggio di output viene visualizzato solo quando vengono soddisfatte determinate condizioni.

Per le espressioni condizionali, è possibile impostare il punto di analisi in modo che restituisca un messaggio quando una determinata condizione è true o quando è stata modificata. Se, ad esempio, si desidera visualizzare il valore del contatore solo durante le iterazioni del ciclo di `for`, è possibile selezionare l'opzione **è true** , quindi digitare `i%2 == 0` nella casella di testo del messaggio.

![L'espressione condizionale è true](../debugger/media/conditionalexpressionistrue.png "L'espressione condizionale è true")

Se si desidera stampare il valore del contatore quando viene modificata l'iterazione del ciclo di `for`, selezionare l'opzione **When Changed** e digitare `i` nella casella di testo del messaggio.

![Espressione condizionale quando viene modificata](../debugger/media/conditionalexpressionwhenchanged.png "Espressione condizionale quando viene modificata")

Il comportamento dell'opzione **When Changed** è diverso per i diversi linguaggi di programmazione.

- Per il codice nativo, il debugger non considera la prima valutazione della condizione come una modifica, quindi non raggiunge il punto di analisi alla prima valutazione.
- Per il codice gestito, il debugger raggiunge il punto di analisi alla prima valutazione dopo la selezione di **modificato** .

Per informazioni più complete sulle espressioni valide che è possibile usare durante l'impostazione delle condizioni, vedere [espressioni nel debugger](expressions-in-the-debugger.md).

### <a name="hit-count"></a>Numero di passaggi
Una condizione di numero di passaggi consente di inviare l'output solo dopo che la riga di codice in cui è impostato il punto di analisi è stata eseguita per un numero di volte specificato.

Per il numero di passaggi è possibile scegliere di generare un messaggio quando la riga di codice in cui è impostato il punto di analisi è stata eseguita un numero di volte uguale a, è un multiplo di o è maggiore o uguale al valore del numero di passaggi specificato. Scegliere l'opzione più adatta alle proprie esigenze e digitare un valore integer nel campo (ad esempio, 5) che rappresenta l'iterazione di interesse.

![Numero di passaggi delle espressioni condizionali](../debugger/media/conditionalexpressionhitcount.png "Numero di passaggi delle espressioni condizionali")

### <a name="filter"></a>Filtro
Per una condizione di filtro, specificare per quali dispositivi, processi o output dei thread viene visualizzato.

![Filtro espressione condizionale](../debugger/media/conditionalexpressionfilter.png "Filtro espressione condizionale")

Elenco di espressioni di filtro:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Racchiudere le stringhe, ad esempio i nomi, tra virgolette doppie. I valori possono essere immessi senza virgolette. È possibile combinare clausole usando `&` (`AND`), `||` (`OR`), `!` (`NOT`) e le parentesi.

## <a name="considerations"></a>Considerazioni

Anche se punti è progettato per semplificare l'esperienza di debug e più semplice, è necessario tenere presenti alcune considerazioni su come usarle.

In alcuni casi, quando si ispeziona una proprietà o un attributo di un oggetto, il relativo valore può cambiare. Non si tratta di un bug causato dalla funzionalità del punto di analisi, ma è importante ricordare che l'uso di punti per controllare gli oggetti non evita queste modifiche accidentali.

Il modo in cui le espressioni vengono valutate nella finestra di messaggio **azione** può essere diverso dalla lingua attualmente utilizzata per lo sviluppo. Per restituire una stringa, ad esempio, non è necessario eseguire il wrapping di un messaggio tra virgolette anche se si utilizza normalmente `Debug.WriteLine()` o `console.log()`. Inoltre, la sintassi di parentesi graffe (`{ }`) per le espressioni di output può essere diversa rispetto alla convenzione per l'output dei valori nel linguaggio di sviluppo. Tuttavia, il contenuto racchiuso tra parentesi graffe (`{ }`) deve comunque essere scritto utilizzando la sintassi del linguaggio di sviluppo.

Se si sta provando a eseguire il debug di un'applicazione in tempo reale e di cercare una funzionalità simile, vedere la funzionalità punto nel Snapshot Debugger. Snapshot debugger è uno strumento utilizzato per analizzare i problemi nelle applicazioni di produzione. Punti consentono inoltre di inviare messaggi al Finestra di output senza dover modificare il codice sorgente e non influiscano sull'applicazione in esecuzione. Per ulteriori informazioni, vedere [debug di un'applicazione Azure Live](../debugger/debug-live-azure-applications.md).

## <a name="see-also"></a>Vedere anche

- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Scrivere codice C# migliore con Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Esaminare prima di tutto il debug](../debugger/debugger-feature-tour.md)
- [Espressioni nel debugger](expressions-in-the-debugger.md)
- [Usare i punti di interruzione](../debugger/using-breakpoints.md)
- [Eseguire il debug di applicazioni Azure attive](../debugger/debug-live-azure-applications.md)
