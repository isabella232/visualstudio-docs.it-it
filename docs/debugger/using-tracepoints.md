---
title: Informazioni di log con punti di traccia | Microsoft Docs
description: Impostare punti di traccia per registrare le informazioni su Output senza modificare o arrestare il codice. È sufficiente specificare una stringa di output sotto la casella di controllo Azione in Punto di interruzione Impostazioni.
ms.custom: SEO-VS-2020
ms.date: 10/28/2019
ms.topic: how-to
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 159754d466f1a9b0113920c2a678bed703600e432ed0e6c8df3fadbb60ddb0c1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419467"
---
# <a name="log-info-to-the-output-window-using-tracepoints-in-visual-studio"></a>Registrare le informazioni nella finestra Output usando i punti di traccia in Visual Studio

I punti di traccia consentono di registrare le informazioni nella finestra Output in condizioni configurabili senza modificare o arrestare il codice. Questa funzionalità è supportata sia per i linguaggi gestiti (C#, Visual Basic, F#) che per il codice nativo, nonché per i linguaggi come JavaScript e Python.

## <a name="let39s-take-an-example"></a>Si&#39;esempio

Il programma di esempio seguente è un ciclo semplice con una variabile contatore che aumenta di uno ogni volta che `for` il ciclo esegue un'altra iterazione.

![Esempio di contatore](../debugger/media/counterexample.png "Esempio di contatore")

## <a name="set-tracepoints-in-source-code"></a>Impostare punti di traccia nel codice sorgente

È possibile impostare punti di traccia specificando una stringa di output sotto la **casella di** controllo Azione nella finestra Impostazioni punto **di** interruzione.

1. Per inizializzare un punto di traccia, fare prima clic sul margine a sinistra del numero di riga in cui si vuole impostare il punto di traccia.

   ![Inizializzazione del punto di interruzione](../debugger/media/breakpointinitialization.png "Inizializzazione del punto di interruzione")

2. Passare il puntatore del mouse sul cerchio rosso e quindi fare clic sull'icona a forma di ingranaggio.
3. Verrà visualizzata la finestra **Impostazioni** punto di interruzione.

   ![Finestra Punto di interruzione](../debugger/media/breakpointwindow.png "Finestra Punto di interruzione")

4. Selezionare la casella **di controllo** Azione.

   ![Casella Azioni selezionate](../debugger/media/checkedactionsbox.png "Casella Azioni selezionate")

   Si noti che il cerchio rosso cambia in un rombo che indica che è stato fatto il passaggio da un punto di interruzione a un punto di traccia.

5. Immettere il messaggio a cui si vuole accedere nella casella di testo **Mostra** un messaggio nella Finestra di output (per informazioni dettagliate, vedere le sezioni successive di questo articolo).

   Il punto di traccia è ora impostato. Fare clic &quot; sul pulsante Chiudi se si vuole solo &quot; registrare alcune informazioni nel Finestra di output.

6. Per aggiungere condizioni che determinano se il messaggio viene visualizzato, selezionare la casella **di controllo** Condizioni.

   ![Casella Condizioni selezionate](../debugger/media/checkedconditionsbox.png "Casella Condizioni selezionate")

   Sono disponibili tre opzioni per le condizioni: **Espressione condizionale**, **Filtro** e **Conteggio risultati**.

## <a name="actions-menu"></a>Menu Azioni

Questo menu consente di registrare un messaggio nella finestra Output. Digitare le stringhe da visualizzare nella finestra di messaggio (non sono necessarie virgolette). Se si desidera visualizzare i valori delle variabili, assicurarsi di racchiuderlo tra parentesi graffe.

Ad esempio, se si vuole visualizzare il valore della variabile nella `counter` console di output, digitare {counter} nella casella di testo del messaggio.

![Messaggio di output del contatore](../debugger/media/counteroutputmessage.png "Messaggio di output del contatore")

Se si fa **clic su Chiudi** e quindi si esegue il debug del programma (**F5**), nella finestra Output viene visualizzato l'output seguente.

![Messaggio azioni in Finestra di output](../debugger/media/actionsmessageinoutputwindow.png "Messaggio delle azioni Finestra di output")

È anche possibile usare parole chiave speciali per visualizzare informazioni più specifiche. Immettere la parola chiave esattamente come illustrato di seguito (usare "$" davanti a ogni parola chiave e tutte le maiuscole per la parola chiave stessa).

| Parola chiave | Elementi visualizzati |
| --- | --- |
| $ADDRESS | Istruzione corrente |
| $CALLER | Scegliere il nome della funzione |
| $CALLSTACK | Stack di chiamate |
| $FUNCTION | Nome della funzione corrente |
| $PID | ID di processo |
| $PNAME | Nome del processo |
| $TID | ID del thread |
| $TNAME   | Nome del thread |
| $TICK | Conteggio tick (da Windows GetTickCount) |

## <a name="conditions-menu"></a>Menu Condizioni

Le condizioni consentono di filtrare i messaggi di output, in modo che siano visualizzati solo in determinati scenari. Sono disponibili tre tipi principali di condizioni.

### <a name="conditional-expression"></a>Espressione condizionale
Per un'espressione condizionale, un messaggio di output viene visualizzato solo quando vengono soddisfatte determinate condizioni.

Per le espressioni condizionali, è possibile impostare il punto di traccia per l'output di un messaggio quando una determinata condizione è true o quando è stata modificata. Ad esempio, se si vuole visualizzare il valore di counter solo durante le iterazioni pari del ciclo, è possibile selezionare l'opzione È true e quindi digitare nella casella di `for` testo del  `i%2 == 0` messaggio.

![L'espressione condizionale è true](../debugger/media/conditionalexpressionistrue.png "L'espressione condizionale è true")

Se si desidera stampare il valore di counter quando cambia l'iterazione del ciclo, selezionare l'opzione Quando modificato e `for` digitare nella casella di testo del  `i` messaggio.

![Espressione condizionale in caso di modifica](../debugger/media/conditionalexpressionwhenchanged.png "Espressione condizionale quando viene modificata")

Il comportamento dell'opzione  **Quando modificato**  è diverso per linguaggi di programmazione diversi.

- Per il codice nativo, il debugger non considera la prima valutazione della condizione come una modifica, quindi non viene raggiunto il punto di traccia alla prima valutazione.
- Per il codice gestito, il debugger raggiunge il punto di traccia alla prima valutazione dopo **l'opzione Quando modificato**  è selezionato.

Per un'analisi più completa delle espressioni valide che è possibile usare durante l'impostazione delle condizioni, vedere [Espressioni nel debugger](expressions-in-the-debugger.md).

### <a name="hit-count"></a>Numero di hit
Una condizione di hit count consente di inviare l'output solo dopo che la riga di codice in cui è impostato il punto di traccia è stata eseguita un numero specificato di volte.

Per il numero di hit, è possibile scegliere di inviare un messaggio quando la riga di codice in cui è impostato il punto di traccia è stata eseguita un numero di volte uguale a, è un multiplo di o è maggiore o uguale al valore del numero di hit specificato. Scegliere l'opzione più adatta alle proprie esigenze e digitare un valore intero nel campo (ad esempio, 5) che rappresenta l'iterazione di interesse.

![Conteggio dei hit delle espressioni condizionali](../debugger/media/conditionalexpressionhitcount.png "Conteggio dei hit delle espressioni condizionali")

### <a name="filter"></a>Filtra
Per una condizione di filtro, specificare per quali dispositivi, processi o thread viene visualizzato l'output.

![Filtro delle espressioni condizionali](../debugger/media/conditionalexpressionfilter.png "Filtro di espressione condizionale")

Elenco di espressioni di filtro:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Racchiudere le stringhe (ad esempio i nomi) tra virgolette doppie. I valori possono essere immessi senza virgolette. È possibile combinare clausole `&` usando ( ), ( ), ( ) e `AND` `||` `OR` `!` `NOT` parentesi.

## <a name="considerations"></a>Considerazioni

Anche se i punti di traccia sono destinati a rendere il debug un'esperienza più semplice e uniforme, è necessario tenere presenti alcune considerazioni quando si tratta di usarli.

In alcuni casi, quando si esamina una proprietà o un attributo di un oggetto, il relativo valore può cambiare. Se il valore cambia durante l'ispezione, non si tratta di un bug causato dalla funzionalità del punto di traccia stessa. Tuttavia, l'uso di punti di traccia per esaminare gli oggetti non evita queste modifiche accidentali.

Il modo in cui le espressioni vengono valutate nella finestra **di** messaggio Azione può essere diverso dal linguaggio attualmente in uso per lo sviluppo. Ad esempio, per l'output di una stringa non è necessario racchiudere un messaggio tra virgolette anche se normalmente si usa `Debug.WriteLine()` o `console.log()` . Inoltre, la sintassi delle parentesi graffe ( ) per le espressioni di output può essere diversa dalla convenzione per l'output dei valori `{ }` nel linguaggio di sviluppo. Tuttavia, il contenuto all'interno delle parentesi graffe ( ) deve comunque essere scritto `{ }` usando la sintassi del linguaggio di sviluppo.

Se si sta tentando di eseguire il debug di un'applicazione in tempo reale e si cerca una funzionalità simile, vedere la funzionalità logpoint nel Snapshot Debugger. Il debugger snapshot è uno strumento usato per analizzare i problemi nelle applicazioni di produzione. I punti di log consentono anche di inviare messaggi al Finestra di output senza dover modificare il codice sorgente e non influiscono sull'applicazione in esecuzione. Per altre informazioni, vedere Eseguire il [debug di un'applicazione Azure in tempo reale.](../debugger/debug-live-azure-applications.md)

## <a name="see-also"></a>Vedi anche

- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Scrivere codice C# migliore usando Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Prima analisi del debug](../debugger/debugger-feature-tour.md)
- [Espressioni nel debugger](expressions-in-the-debugger.md)
- [Usare i punti di interruzione](../debugger/using-breakpoints.md)
- [Eseguire il debug di applicazioni Azure in tempo reale](../debugger/debug-live-azure-applications.md)
