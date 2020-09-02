---
title: Visualizzare i thread nella finestra stack in parallelo | Microsoft Docs
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9728346bc4c6d805bb0febd3a0d5bef0ed809a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62902420"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>Visualizzare i thread e le attività nella finestra stack in parallelo (C#, Visual Basic, C++)

La finestra **stack in parallelo** è utile per il debug di applicazioni multithread. Sono disponibili diverse visualizzazioni:

- [Visualizzazione thread Mostra](#threads-view) informazioni sullo stack di chiamate per tutti i thread nell'app. È possibile spostarsi tra i thread e gli stack frame in tali thread.

- [Visualizzazione attività Mostra](#tasks-view) informazioni sullo stack di chiamate centrate sulle attività.
  - In codice gestito, visualizzazione **attività** Mostra gli stack di chiamate degli <xref:System.Threading.Tasks.Task?displayProperty=fullName> oggetti.
  - Nel codice nativo, la visualizzazione **attività** Mostra gli stack di chiamate di [gruppi di attività](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [algoritmi paralleli](/cpp/parallel/concrt/parallel-algorithms), [agenti asincroni](/cpp/parallel/concrt/asynchronous-agents)e [attività leggere](/cpp/parallel/concrt/task-scheduler-concurrency-runtime).

- [Visualizzazione metodo consente](#method-view) di trasformare lo stack di chiamate su un metodo selezionato.

## <a name="use-the-parallel-stacks-window"></a>Usare la finestra Stack in parallelo

Per aprire la finestra **stack in parallelo** , è necessario trovarsi in una sessione di debug. Selezionare **debug**  >  **Windows**  >  **stack in parallelo**di Windows.

### <a name="toolbar-controls"></a>Controlli della barra degli strumenti

La finestra **stack in parallelo** dispone dei seguenti controlli della barra degli strumenti:

![Barra degli strumenti nella finestra Stack in parallelo](../debugger/media/parallel_stackstoolbar.png "Barra degli strumenti stack in parallelo")

|Icona|Controllo|Descrizione|
|-|-|-|
|![Casella combinata Thread/Attività](media/parallel_toolbar1.png "Casella combinata Thread/Attività")|**Thread** / Casella combinata **attività**|Consente di passare dalla visualizzazione degli stack di chiamate dei thread alla visualizzazione degli stack di chiamate delle attività e viceversa. Per altre informazioni, vedere [Visualizzazione Attività](#tasks-view) e [Visualizzazione Thread](#threads-view).|
|![Mostra solo icona con flag](media/parallel_toolbar2.png "Mostra solo icona con flag")|Mostra solo con contrassegno|Mostra gli stack di chiamate solo per i thread contrassegnati in altre finestre del debugger, ad esempio la finestra **thread GPU** e la finestra espressione di **controllo in parallelo** .|
|![Icona Visualizza/Nascondi metodo](media/parallel_toolbar3.png "Icona Visualizza/Nascondi metodo")|Attiva/Disattiva **visualizzazione metodo**|Passa tra le visualizzazioni dello stack di chiamate e la **visualizzazione del metodo**. Per altre informazioni, vedere [Visualizzazione metodo](#method-view).|
|![Scorri automaticamente fino all'icona corrente](media/parallel_toolbar4.png "Scorri automaticamente fino all'icona corrente")|Scorrimento automatico a stack frame corrente|Scorre lo scorrimento automatico del grafico in modo che l'stack frame corrente sia in visualizzazione. Questa funzionalità è utile quando si modifica la stack frame corrente da altre finestre o quando si raggiunge un nuovo punto di interruzione in grafici di grandi dimensioni.|
|![Icona Mostra/Nascondi zoom](media/parallel_toolbar5.png "Icona Mostra/Nascondi zoom")|Attiva/Disattiva controllo zoom|Mostra o nasconde il controllo zoom a sinistra della finestra. <br /><br />Indipendentemente dalla visibilità del controllo zoom, è anche possibile ingrandire premendo **CTRL** e ruotando la rotellina del mouse oppure premendo **CTRL** + **MAIUSC** + **+** per eseguire lo zoom avanti e **CTRL** + **MAIUSC** + **-** per eseguire lo zoom indietro. |

### <a name="stack-frame-icons"></a>Icone dello stack frame
Le icone seguenti forniscono informazioni sugli stack frame attivi e correnti in tutte le visualizzazioni:

|Icona|Descrizione|
|-|-|
|![Freccia gialla](media/icon_parallelyellowarrow.gif)|Indica la posizione corrente (attiva stack frame) del thread corrente.|
|![Icona thread](media/icon_parallelthreads.gif)|Indica la posizione corrente (attiva stack frame) di un thread non corrente.|
|![Freccia verde](media/icon_parallelgreenarrow.gif)|Indica il stack frame corrente (contesto del debugger corrente). Il nome del metodo è in grassetto ovunque venga visualizzato.|

### <a name="context-menu-items"></a>Voci del menu di scelta rapida
Le voci del menu di scelta rapida seguenti sono disponibili quando si fa clic con il pulsante destro del mouse su un metodo nella visualizzazione **thread** o nella visualizzazione **attività** . Gli ultimi sei elementi corrispondono alla [finestra stack di chiamate](how-to-use-the-call-stack-window.md).

![Menu di scelta rapida nella finestra Stack in parallelo](../debugger/media/parallel_contmenu.png "Menu di scelta rapida nella finestra Stack in parallelo")

|Voce di menu|Descrizione|
|-|-|
|**Bandiera**|Contrassegna l'elemento selezionato.|
|**Rimuovi flag**|Rimuove il flag dall'elemento selezionato.|
|**Freeze**|Blocca l'elemento selezionato.|
|**Sblocca**|Sblocca l'elemento selezionato.|
|**Passa al frame**|Uguale al comando di menu corrispondente nella finestra **stack di chiamate** . Tuttavia, nella finestra **stack in parallelo** , un metodo può trovarsi in diversi frame. È possibile selezionare il frame desiderato nel sottomenu per questo elemento. Se uno degli stack frame è nel thread corrente, il frame è selezionato per impostazione predefinita nel sottomenu.|
|**Vai a attività** o **Vai al thread**|Passa alla visualizzazione **attività** o **thread** e mantiene lo stesso stack frame evidenziato.|
|**Vai a codice sorgente**|Passa alla posizione corrispondente nella finestra del codice sorgente. |
|**Vai a disassembly**|Passa alla posizione corrispondente nella finestra **Disassembly** .|
|**Mostra codice esterno**|Mostra o nasconde il codice esterno.|
|**Visualizzazione esadecimale**|Consente di passare dalla visualizzazione decimale a quella esadecimale e viceversa.|
|**Mostra thread nell'origine**|Contrassegna il percorso del thread nella finestra del codice sorgente. |
|**Informazioni sul caricamento simboli**|Apre la finestra di dialogo **informazioni sul caricamento dei simboli** .|
|**Impostazioni simboli**|Apre la finestra di dialogo **Impostazioni simboli** . |

## <a name="threads-view"></a>visualizzazione thread

Nella visualizzazione **thread** il stack frame e il percorso di chiamata del thread corrente sono evidenziati in blu. La posizione corrente del thread è indicata dalla freccia gialla.

Per modificare la stack frame corrente, fare doppio clic su un metodo diverso. Questo potrebbe anche cambiare il thread corrente, a seconda che il metodo selezionato faccia parte del thread corrente o di un altro thread.

Quando il grafico della visualizzazione dei **thread** è troppo grande per essere inserito nella finestra, nella finestra viene visualizzato il controllo di **visualizzazione occhio** di un uccello. È possibile spostare il frame nel controllo per passare a diverse parti del grafico.

La figura seguente mostra un thread che passa da principale a una transizione di codice gestito a codice nativo. Sei thread sono nel metodo corrente. Uno continua a thread. Sleep e un altro continua a console. WriteLine e quindi a SyncTextWriter. WriteLine.

 ![Visualizzazione thread nella finestra Stack in parallelo](../debugger/media/parallel_stack1.png "Visualizzazione thread nella finestra Stack in parallelo")

Nella tabella seguente vengono descritte le principali funzionalità della visualizzazione **thread** :

|Callout|Nome dell'elemento|Descrizione|
|-|-|-|
|1|Segmento o nodo dello stack di chiamate|Contiene una serie di metodi per uno o più thread. Se al frame non sono connesse linee della freccia, il frame Mostra l'intero percorso di chiamata per i thread.|
|2|Evidenziazione blu|Indica il percorso di chiamate del thread corrente.|
|3|Righe della freccia|Connettono i nodi per costituire l'intero percorso di chiamate per i thread.|
|4|Intestazione del nodo|Mostra il numero di processi e thread per il nodo.|
|5|Metodo|Rappresenta uno o più stack frame nello stesso metodo.|
|6|Descrizione comando sul metodo|Viene visualizzato quando si passa il mouse su un metodo. Nella visualizzazione **thread** la descrizione comando Mostra tutti i thread, in una tabella simile alla finestra **thread** . |

## <a name="tasks-view"></a>Visualizzazione Attività
Se l'app usa <xref:System.Threading.Tasks.Task?displayProperty=fullName> oggetti (codice gestito) o `task_handle` oggetti (codice nativo) per esprimere il parallelismo, è possibile usare la visualizzazione **attività** . La visualizzazione **Attività** mostra gli stack di chiamate delle attività anziché dei thread.

Nella visualizzazione **attività** :

- Gli stack di chiamate dei thread che non eseguono attività non vengono visualizzati.
- Gli stack di chiamate dei thread che eseguono attività vengono ritagliati visivamente nella parte superiore e inferiore per visualizzare i frame più rilevanti per le attività.
- Quando più attività si trovano in un thread, gli stack di chiamate di tali attività vengono visualizzati in nodi separati.

Per visualizzare un intero stack di chiamate, tornare alla visualizzazione **thread** facendo clic con il pulsante destro del mouse in una stack frame e selezionando **Vai al thread**.

Nella figura seguente viene illustrata la visualizzazione **thread** nella parte superiore e la visualizzazione **attività** corrispondente in basso.

![Viste thread e attività](../debugger/media/parallel_threads-tasks.png "Viste thread e attività")

Passare il puntatore del mouse su un metodo per visualizzare una descrizione comando con informazioni aggiuntive. Nella visualizzazione **attività** la descrizione comando Mostra tutte le attività in una tabella simile alla finestra **attività** .

Nell'immagine seguente viene illustrata la descrizione comando per un metodo nella visualizzazione **thread** nella parte superiore e per la visualizzazione **attività** corrispondente in basso.

![Descrizioni comando per thread e attività](../debugger/media/parallel_threads-tasks-tooltips.png "Descrizioni comando per thread e attività")

## <a name="method-view"></a>Visualizzazione metodo
Dalla visualizzazione **thread** o dalla visualizzazione **attività** è possibile eseguire il pivot del grafico sul metodo corrente selezionando l'icona **Visualizza/Nascondi metodo** sulla barra degli strumenti. La **visualizzazione Metodo** mostra immediatamente tutti i metodi in tutti i thread che chiamano o sono chiamati dal metodo corrente. Nella figura seguente viene illustrato il modo in cui le stesse informazioni vengono esaminate nella visualizzazione **thread** sulla sinistra e nella **visualizzazione metodo** a destra.

![Visualizzazione thread e visualizzazione metodo](../debugger/media/parallel_methodview.png "Visualizzazione thread e visualizzazione metodo")

Se si passa a una nuova stack frame, questo metodo viene reso il metodo corrente e la **visualizzazione metodo** Mostra tutti i chiamanti e i chiamanti per il nuovo metodo. È possibile che, in conseguenza a ciò, alcuni thread compaiano o scompaiano dalla visualizzazione, a seconda che il metodo sia visualizzato nei relativi stack di chiamate. Per tornare alla visualizzazione dello stack di chiamate, selezionare di nuovo l'icona della barra degli strumenti **visualizzazione metodo** .

## <a name="see-also"></a>Vedere anche
- [Introduzione al debug di un'applicazione multithreading](../debugger/get-started-debugging-multithreaded-apps.md)
- [Procedura dettagliata: Eseguire il debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
- [Programmazione parallela](/dotnet/standard/parallel-programming/index)
- [Usare la finestra Attività](../debugger/using-the-tasks-window.md)
- [Classe Task](../extensibility/debugger/task-class-internal-members.md)
