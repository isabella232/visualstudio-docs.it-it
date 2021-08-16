---
title: Visualizzare i thread nella finestra Stack in parallelo | Microsoft Docs
description: Usare stack paralleli per eseguire il debug di applicazioni multithreading. È possibile visualizzare le informazioni sullo stack per tutti i thread e le informazioni sullo stack di chiamate centrato sulle attività.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d1fd19de0c9673835a0a00bf5453a15fad16f9c3d32c1b2dd2b9d8e019ef5e9d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121361683"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>Visualizzare thread e attività nella finestra Stack in parallelo (C#, Visual Basic, C++)

La **finestra Stack in parallelo** è utile per il debug di applicazioni multithreading. Include diverse visualizzazioni:

- [La visualizzazione Thread](#threads-view) mostra le informazioni sullo stack di chiamate per tutti i thread nell'app. È possibile spostarsi tra thread e stack frame in tali thread.

- [La visualizzazione Attività mostra](#tasks-view) le informazioni sullo stack di chiamate centrato sulle attività.
  - Nel codice gestito la **visualizzazione Attività** mostra gli stack di chiamate degli <xref:System.Threading.Tasks.Task?displayProperty=fullName> oggetti.
  - Nel codice nativo la **visualizzazione Attività** mostra gli stack di chiamate di gruppi di [attività,](/cpp/parallel/concrt/task-parallelism-concurrency-runtime) [algoritmi paralleli,](/cpp/parallel/concrt/parallel-algorithms)agenti [asincroni](/cpp/parallel/concrt/asynchronous-agents)e [attività leggere.](/cpp/parallel/concrt/task-scheduler-concurrency-runtime)

- [La visualizzazione Metodo](#method-view) consente di convertire lo stack di chiamate in base a un metodo selezionato.

## <a name="use-the-parallel-stacks-window"></a>Usare la finestra Stack in parallelo

Per aprire la **finestra Stack in** parallelo, è necessario essere in una sessione di debug. Selezionare **Debug**  >  **Windows**  >  **Parallel Stacks (Stack paralleli).**

### <a name="toolbar-controls"></a>Controlli della barra degli strumenti

La **finestra Stack in parallelo** include i controlli della barra degli strumenti seguenti:

![Barra degli strumenti nella finestra Stack in parallelo](../debugger/media/parallel_stackstoolbar.png "Barra degli strumenti Stack paralleli")

|Icona|Controllo|Descrizione|
|-|-|-|
|![Casella combinata Thread/Attività](media/parallel_toolbar1.png "Casella combinata Thread/Attività")|**Thread** / **Casella combinata** Attività|Consente di passare dalla visualizzazione degli stack di chiamate dei thread alla visualizzazione degli stack di chiamate delle attività e viceversa. Per altre informazioni, vedere [Visualizzazione Attività](#tasks-view) e [Visualizzazione Thread](#threads-view).|
|![Icona Mostra solo contrassegnati](media/parallel_toolbar2.png "Mostra solo icona contrassegnata")|Mostra solo con contrassegno|Mostra gli stack di chiamate solo per i thread contrassegnati in altre finestre del debugger, ad esempio la finestra Thread **GPU** e la **finestra Espressioni di controllo** in parallelo.|
|![Icona Attiva/Disattiva visualizzazione metodo](media/parallel_toolbar3.png "Icona Attiva/Disattiva visualizzazione metodo")|Attiva/Disattiva **visualizzazione metodo**|Consente di passare da una visualizzazione stack di chiamate a **una visualizzazione metodi e da una visualizzazione metodi all'altra.** Per altre informazioni, vedere [Visualizzazione metodo](#method-view).|
|![Icona Di scorrimento automatico fino alla versione corrente](media/parallel_toolbar4.png "Icona Scorrimento automatico fino a Corrente")|Scorrimento automatico a stack frame corrente|Scorre automaticamente il grafico in modo che sia stack frame corrente. Questa funzionalità è utile quando si modifica l'stack frame corrente da altre finestre o quando si preme un nuovo punto di interruzione in grafici di grandi dimensioni.|
|![Icona Attiva/Disattiva zoom](media/parallel_toolbar5.png "Attivare/disattivare l'icona Zoom")|Attiva/Disattiva controllo zoom|Mostra o nasconde il controllo zoom a sinistra della finestra. <br /><br />Indipendentemente dalla visibilità del controllo zoom, è anche possibile eseguire lo zoom premendo **CTRL** e ruotando la rotellina del mouse oppure premendo **CTRL** MAIUSC per eseguire lo zoom avanti e CTRL MAIUSC per +  + **+** eseguire  +  + **-** lo zoom indietro. |

### <a name="stack-frame-icons"></a>Icone stack frame
Le icone seguenti forniscono informazioni sugli stack frame attivi e correnti in tutte le visualizzazioni:

|Icona|Descrizione|
|-|-|
|![Freccia gialla](media/icon_parallelyellowarrow.gif)|Indica la posizione corrente (stack frame) del thread corrente.|
|![Icona Thread](media/icon_parallelthreads.gif)|Indica la posizione corrente (stack frame) di un thread non corrente.|
|![Freccia verde](media/icon_parallelgreenarrow.gif)|Indica l'oggetto stack frame (contesto del debugger corrente). Il nome del metodo è in grassetto ovunque venga visualizzato.|

### <a name="context-menu-items"></a>Voci del menu di scelta rapida
Le voci del menu di scelta rapida seguenti sono disponibili quando si fa clic con il pulsante destro del mouse su un metodo nella **visualizzazione** Thread **o Attività.** Gli ultimi sei elementi sono gli stessi della finestra [Stack di chiamate](how-to-use-the-call-stack-window.md).

![Menu di scelta rapida nella finestra Stack in parallelo](../debugger/media/parallel_contmenu.png "Menu di scelta rapida nella finestra Stack in parallelo")

|Voce di menu|Descrizione|
|-|-|
|**Contrassegno**|Contrassegna l'elemento selezionato.|
|**Rimuovi flag**|Rimuove il flag dall'elemento selezionato.|
|**Freeze**|Blocca l'elemento selezionato.|
|**Disgelo**|Sblocca l'elemento selezionato.|
|**Passa al frame**|Uguale al comando di menu corrispondente nella **finestra Stack di** chiamate. Tuttavia, nella finestra **Stack in parallelo** un metodo può essere in più frame. È possibile selezionare il frame desiderato nel sottomenu per questo elemento. Se uno degli stack frame si trova nel thread corrente, tale frame viene selezionato per impostazione predefinita nel sottomenu.|
|**Passare ad Attività** o **Vai a thread**|Passa alla **visualizzazione Attività** o **Thread** e mantiene evidenziate stack frame attività.|
|**Vai a codice sorgente**|Passa alla posizione corrispondente nella finestra del codice sorgente. |
|**Vai a disassembly**|Passa al percorso corrispondente nella **finestra Disassembly.**|
|**Mostra codice esterno**|Mostra o nasconde il codice esterno.|
|**Visualizzazione esadecimale**|Consente di passare dalla visualizzazione decimale a quella esadecimale e viceversa.|
|**Mostra thread nell'origine**|Contrassegna la posizione del thread nella finestra del codice sorgente. |
|**Informazioni sul caricamento simboli**|Apre la **finestra di dialogo Informazioni sul caricamento** simboli .|
|**Simbolo Impostazioni**|Apre la **finestra di dialogo Impostazioni** simboli . |

## <a name="threads-view"></a>visualizzazione thread

Nella **visualizzazione** Thread le stack frame e il percorso di chiamata del thread corrente sono evidenziati in blu. La posizione corrente del thread è indicata dalla freccia gialla.

Per modificare l'stack frame corrente, fare doppio clic su un metodo diverso. Questo potrebbe anche cambiare il thread corrente, a seconda che il metodo selezionato sia parte del thread corrente o di un altro thread.

Quando il **grafico della** visualizzazione Thread è troppo  grande per rientrare nella finestra, nella finestra viene visualizzato un controllo Visualizzazione a occhio. È possibile spostare il frame nel controllo per passare a diverse parti del grafico.

La figura seguente mostra un thread che passa da Main a Managed a Native code transition. Nel metodo corrente sono presenti sei thread. Uno continua a Thread.Sleep e un altro continua a Console.WriteLine e quindi a SyncTextWriter.WriteLine.

 ![Visualizzazione thread nella finestra Stack in parallelo](../debugger/media/parallel_stack1.png "Visualizzazione thread nella finestra Stack in parallelo")

La tabella seguente descrive le funzionalità principali della **visualizzazione** Thread:

|Callout|Nome dell'elemento|Descrizione|
|-|-|-|
|1|Segmento o nodo dello stack di chiamate|Contiene una serie di metodi per uno o più thread. Se al frame non sono collegate linee di freccia, il frame mostra l'intero percorso di chiamata per i thread.|
|2|Evidenziazione blu|Indica il percorso di chiamate del thread corrente.|
|3|Righe della freccia|Connettono i nodi per costituire l'intero percorso di chiamate per i thread.|
|4|Intestazione del nodo|Visualizza il numero di processi e thread per il nodo.|
|5|Metodo|Rappresenta uno o più stack frame nello stesso metodo.|
|6|Descrizione comando sul metodo|Viene visualizzato quando si passa il mouse su un metodo. Nella **visualizzazione Thread** la descrizione comando mostra tutti i thread, in una tabella simile alla **finestra** Thread. |

## <a name="tasks-view"></a>Visualizzazione Attività
Se l'app usa oggetti (codice gestito) o oggetti (codice nativo) per esprimere <xref:System.Threading.Tasks.Task?displayProperty=fullName> `task_handle` il parallelismo, è possibile usare **la visualizzazione** Attività. La visualizzazione **Attività** mostra gli stack di chiamate delle attività anziché dei thread.

Nella **visualizzazione** Attività:

- Gli stack di chiamate dei thread che non eseguono attività non vengono visualizzati.
- Gli stack di chiamate dei thread che eseguono attività vengono tagliati visivamente nella parte superiore e inferiore, per visualizzare i frame più rilevanti per le attività.
- Quando in un thread sono presenti più attività, gli stack di chiamate di tali attività vengono visualizzati in nodi separati.

Per visualizzare un intero stack di chiamate, tornare **alla** visualizzazione Thread facendo clic con il pulsante destro del mouse su un stack frame e scegliendo Vai **a thread**.

La figura seguente mostra la **visualizzazione Thread** nella parte superiore e la **visualizzazione** Attività corrispondente nella parte inferiore.

![Visualizzazioni Thread e Attività](../debugger/media/parallel_threads-tasks.png "Visualizzazioni Thread e Attività")

Passare il mouse su un metodo per visualizzare una descrizione comando con informazioni aggiuntive. Nella **visualizzazione** Attività la descrizione comando mostra tutte le attività in una tabella simile alla **finestra** Attività.

L'immagine seguente mostra la descrizione comando per un metodo nella visualizzazione **Thread** nella parte superiore e per la visualizzazione **Attività** corrispondente nella parte inferiore.

![Descrizioni comando di thread e attività](../debugger/media/parallel_threads-tasks-tooltips.png "Descrizioni comando di thread e attività")

## <a name="method-view"></a>Visualizzazione metodo
Dalla visualizzazione **Thread** o **Attività** è possibile eseguire il pivot del grafico sul metodo corrente selezionando l'icona **Attiva/Disattiva** visualizzazione metodo sulla barra degli strumenti. La **visualizzazione Metodo** mostra immediatamente tutti i metodi in tutti i thread che chiamano o sono chiamati dal metodo corrente. La figura seguente mostra l'aspetto delle stesse informazioni nella **visualizzazione Thread** a sinistra e in **Visualizzazione metodi** a destra.

![Visualizzazione Thread e Visualizzazione metodi](../debugger/media/parallel_methodview.png "Visualizzazione Thread e Visualizzazione metodi")

Se si passa a un nuovo stack frame, si imposta tale  metodo come metodo corrente e Visualizzazione metodi mostra tutti i chiamanti e i chiamato per il nuovo metodo. È possibile che, in conseguenza a ciò, alcuni thread compaiano o scompaiano dalla visualizzazione, a seconda che il metodo sia visualizzato nei relativi stack di chiamate. Per tornare alla visualizzazione stack di chiamate, selezionare di nuovo **l'icona della** barra degli strumenti Visualizzazione metodi.

## <a name="see-also"></a>Vedi anche
- [Introduzione al debug di un'applicazione multithreading](../debugger/get-started-debugging-multithreaded-apps.md)
- [Procedura dettagliata: Eseguire il debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Debug di codice gestito](../debugger/debugging-managed-code.md)
- [Programmazione parallela](/dotnet/standard/parallel-programming/index)
- [Usare la finestra Attività](../debugger/using-the-tasks-window.md)
- [Classe di attività](../extensibility/debugger/task-class-internal-members.md)
