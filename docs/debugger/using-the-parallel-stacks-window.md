---
title: Visualizzare i thread nella finestra Stack in parallelo | Microsoft Docs
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
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712541"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>Visualizza attività e i thread nella finestra Stack in parallelo (C#, Visual Basic, C++)

Il **stack in parallelo** finestra è utile per il debug di applicazioni multithreading. Include diverse visualizzazioni:

- [Visualizzazione thread](#threads-view) Mostra le informazioni sullo stack di chiamate per tutti i thread nell'app. È possibile spostarsi tra thread e stack frame nei thread.

- [Visualizzazione attività](#tasks-view) Mostra informazioni sullo stack di chiamate al centro attività.
  - Nel codice gestito **attività** visualizzazione Mostra gli stack di chiamate di <xref:System.Threading.Tasks.Task?displayProperty=fullName> oggetti.
  - Nel codice nativo **attività** visualizzazione Mostra gli stack di chiamate di [gruppi di attività](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [algoritmi paralleli](/cpp/parallel/concrt/parallel-algorithms), [agenti asincroni](/cpp/parallel/concrt/asynchronous-agents)e [attività leggere](/cpp/parallel/concrt/task-scheduler-concurrency-runtime).

- [Visualizzazione metodo](#method-view) consente di alternare tra lo stack di chiamate su un metodo selezionato.

## <a name="use-the-parallel-stacks-window"></a>Usare la finestra Stack in parallelo

Per aprire la **stack in parallelo** finestra, è necessario essere in una sessione di debug. Selezionare **Debug** > **Windows** > **stack in parallelo**.

### <a name="toolbar-controls"></a>Controlli della barra degli strumenti

Il **stack in parallelo** finestra dispone di controlli della barra degli strumenti seguenti:

![Barra degli strumenti nella finestra Stack in parallelo](../debugger/media/parallel_stackstoolbar.png "barra degli strumenti stack in parallelo")

|Icona|Control|Description|
|-|-|-|
|![Casella combinata thread/attività](media/parallel_toolbar1.png "casella combinata thread/attività")|**Thread**/**attività** pole se seznamem|Consente di passare dalla visualizzazione degli stack di chiamate dei thread alla visualizzazione degli stack di chiamate delle attività e viceversa. Per altre informazioni, vedere [Visualizzazione Attività](#tasks-view) e [Visualizzazione Thread](#threads-view).|
|![Mostra icona solo con contrassegno](media/parallel_toolbar2.png "icona Mostra solo con contrassegno")|Mostra solo con contrassegno|Mostra gli stack di chiamate per i thread contrassegnati in altre finestre del debugger, ad esempio la **thread GPU** finestra e il **espressioni di controllo parallela** finestra.|
|![Icona Attiva/disattiva visualizzazione metodo](media/parallel_toolbar3.png "icona Attiva/disattiva visualizzazione metodo")|Attiva/Disattiva **visualizzazione metodo**|Passa tra visualizzazioni dello stack di chiamate e **visualizzazione metodo**. Per altre informazioni, vedere [Visualizzazione metodo](#method-view).|
|![Scorrimento automatico a icona corrente](media/parallel_toolbar4.png "scorrimento automatico a icona corrente")|Scorrimento automatico a stack frame corrente|Il grafico scorre automaticamente in modo che lo stack frame corrente è nella visualizzazione. Questa funzionalità è utile quando si modifica lo stack frame corrente da altre finestre o quando si raggiunge un nuovo punto di interruzione in grafi di grandi dimensioni.|
|![Icona Zoom attiva/disattiva](media/parallel_toolbar5.png "icona Attiva/Disattiva Zoom")|Attiva/Disattiva controllo zoom|Mostra o nasconde il controllo zoom a sinistra della finestra. <br /><br />Indipendentemente dalla visibilità del controllo zoom, è inoltre possibile ingrandire premendo **Ctrl** e l'attivazione della rotellina del mouse oppure premendo **Ctrl**+**MAIUSC** + **+** per eseguire lo zoom avanti e **Ctrl**+**MAIUSC** + **-** Per eseguire lo zoom indietro. |

### <a name="stack-frame-icons"></a>Icone di stack Frame
Le icone seguenti forniscono informazioni sui frame dello stack attivi e correnti in tutte le visualizzazioni:

|Icona|Description|
|-|-|
|![Freccia gialla](media/icon_parallelyellowarrow.gif)|Indica la posizione corrente (stack frame attivo) del thread corrente.|
|![Icona thread](media/icon_parallelthreads.gif)|Indica la posizione corrente (stack frame attivo) di un thread non correnti.|
|![Freccia verde](media/icon_parallelgreenarrow.gif)|Indica lo stack frame corrente (il contesto di debug corrente). Il nome del metodo è in grassetto ovunque sia presente.|

### <a name="context-menu-items"></a>Voci del menu di scelta rapida
Sono disponibili le seguenti voci di menu di scelta rapida facendo clic su un metodo in **thread** visualizzazione oppure **attività** visualizzazione. Gli ultimi sei elementi sono uguali a quelle di [finestra Stack di chiamate](how-to-use-the-call-stack-window.md).

![Menu di scelta rapida nella finestra Stack in parallelo](../debugger/media/parallel_contmenu.png "menu di scelta rapida nella finestra Stack in parallelo")

|Voce di menu|Description|
|-|-|
|**Flag**|Contrassegna l'elemento selezionato.|
|**Rimuovi flag**|Rimuove il flag dall'elemento selezionato.|
|**Blocca**|Blocca l'elemento selezionato.|
|**Sblocca**|Sblocca l'elemento selezionato.|
|**Passa al frame**|Stesso come il menu corrispondente comando di **Stack di chiamate** finestra. Tuttavia, nelle **stack in parallelo** finestra, potrebbe essere un metodo in frame diversi. È possibile selezionare il fotogramma desiderato nel sottomenu per questo elemento. Se uno degli stack frame nel thread corrente, quel frame viene selezionata per impostazione predefinita nel sottomenu.|
|**Passare all'attività** o **passa a Thread**|Consente di attivare i **attività** o **thread** Vista e mantiene lo stesso stack frame evidenziato.|
|**Vai a codice sorgente**|Passa alla posizione corrispondente nella finestra del codice sorgente. |
|**Vai a disassembly**|Passa alla posizione corrispondente nel **Disassembly** finestra.|
|**Mostra codice esterno**|Mostra o nasconde il codice esterno.|
|**Visualizzazione esadecimale**|Consente di passare dalla visualizzazione decimale a quella esadecimale e viceversa.|
|**Mostra thread nell'origine**|Contrassegna la posizione del thread nella finestra del codice sorgente. |
|**Informazioni sul caricamento simboli**|Apre la **informazioni sul caricamento simboli** nella finestra di dialogo.|
|**Impostazioni simboli**|Apre la **impostazioni simboli** nella finestra di dialogo. |

## <a name="threads-view"></a>visualizzazione thread

Nelle **thread** consente di visualizzare, lo stack frame e il percorso di chiamate del thread corrente sono evidenziati in blu. La posizione corrente del thread è indicata dalla freccia gialla.

Per modificare lo stack frame corrente, fare doppio clic su un altro metodo. Ciò potrebbe passare anche il thread corrente, a seconda che il metodo selezionato sia parte del thread corrente o un altro thread.

Quando la **thread** visualizzazione grafico è troppo grande per rientrare nella finestra di un **assaggio** controllo viene visualizzato nella finestra. È possibile spostare il frame del controllo per passare a diverse parti del grafico.

La figura seguente mostra un thread che va da Main a Managed per eseguire la transizione di codice nativo. Sei thread sono nel metodo corrente. Uno continua a thread. Sleep e un altro continua a console. WriteLine e quindi a SyncTextWriter.WriteLine.

 ![Visualizzazione nella finestra Stack in parallelo thread](../debugger/media/parallel_stack1.png "visualizzazione nella finestra Stack in parallelo thread")

La tabella seguente descrive le principali funzionalità dei **thread** Vista:

|Callout|Nome elemento|Description|
|-|-|-|
|1|Segmento o nodo dello stack di chiamate|Contiene una serie di metodi per uno o più thread. Se il frame non contiene alcuna riga freccia connessa a esso, il frame viene illustrato l'intero percorso di chiamate per i thread.|
|2|Evidenziazione blu|Indica il percorso di chiamate del thread corrente.|
|3|Righe della freccia|Connettono i nodi per costituire l'intero percorso di chiamate per i thread.|
|4|Intestazione del nodo|Mostra il numero di processi e thread per il nodo.|
|5|Metodo|Rappresenta uno o più stack frame nello stesso metodo.|
|6|Descrizione comando sul metodo|Viene visualizzata quando si passa il mouse su un metodo. Nelle **thread** visualizzazione, la descrizione comando Mostra tutti i thread, in una tabella simile al **thread** finestra. |

## <a name="tasks-view"></a>Visualizzazione Attività
Se l'app Usa <xref:System.Threading.Tasks.Task?displayProperty=fullName> oggetti (codice gestito) oppure `task_handle` oggetti (codice nativo) per esprimere il parallelismo, è possibile usare **attività** visualizzazione. La visualizzazione **Attività** mostra gli stack di chiamate delle attività anziché dei thread.

Nelle **attività** Vista:

- Non vengono visualizzati gli stack di chiamate dei thread che non sono in esecuzione attività.
- Gli stack di chiamate dei thread che eseguono le attività sono visivamente tagliati nella parte superiore e inferiore, per mostrare i frame più rilevanti per le attività.
- Quando più attività sono in un unico thread, gli stack di chiamate di queste attività vengono visualizzati in nodi separati.

Per visualizzare un intero stack di chiamate, tornare a **thread** vista facendo clic in uno stack frame e selezionando **passa a Thread**.

La figura seguente mostra le **thread** visualizzazione in alto e il corrispondente **attività** visualizzazione nella parte inferiore.

![Le visualizzazioni di thread e attività](../debugger/media/parallel_threads-tasks.png "visualizzazioni di thread e attività")

Passare il mouse su un metodo per visualizzare una descrizione comando con informazioni aggiuntive. Nelle **attività** visualizzazione, la descrizione comando Mostra tutte le attività in una tabella simile al **attività** finestra.

L'immagine seguente mostra la descrizione comando per un metodo nel **thread** visualizzazione nella parte superiore e per il corrispondente **attività** visualizzazione nella parte inferiore.

![Le descrizioni comandi thread e attività](../debugger/media/parallel_threads-tasks-tooltips.png "descrizioni comandi di thread e attività")

## <a name="method-view"></a>Visualizzazione metodo
Da una **thread** view o **attività** visualizzazione, è possibile ruotare il grafico sul metodo corrente, selezionare il **attiva/disattiva visualizzazione metodo** icona sulla barra degli strumenti. La **visualizzazione Metodo** mostra immediatamente tutti i metodi in tutti i thread che chiamano o sono chiamati dal metodo corrente. La figura seguente mostra come le stesse informazioni appaiono **thread** Visualizza a sinistra e nella **visualizzazione metodo** sulla destra.

![Metodo e visualizzazione dei thread](../debugger/media/parallel_methodview.png "thread del metodo e vista")

Se si passa a un nuovo stack frame, è rendere tale metodo il metodo corrente, e **visualizzazione metodo** Mostra tutti i chiamanti e chiamati per il nuovo metodo. È possibile che, in conseguenza a ciò, alcuni thread compaiano o scompaiano dalla visualizzazione, a seconda che il metodo sia visualizzato nei relativi stack di chiamate. Per tornare alla visualizzazione dello stack di chiamate, selezionare la **visualizzazione metodo** nuovamente clic sull'icona della barra degli strumenti.

## <a name="see-also"></a>Vedere anche
- [Iniziare il debug di un'applicazione multithreading](../debugger/get-started-debugging-multithreaded-apps.md)
- [Procedura dettagliata: Eseguire il debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Debug di codice gestito](../debugger/debugging-managed-code.md)
- [Programmazione parallela](/dotnet/standard/parallel-programming/index)
- [Usare la finestra Attività](../debugger/using-the-tasks-window.md)
- [Classe Task](../extensibility/debugger/task-class-internal-members.md)
