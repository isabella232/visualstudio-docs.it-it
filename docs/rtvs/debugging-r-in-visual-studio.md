---
title: Debug di codice R
description: Visual Studio offre un'esperienza di debug completa per R, inclusi punti di interruzione, collegamenti, stack di chiamate e ispezione delle variabili.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 98dcbaaeb6f330cda3a14cf8c32afe403b50aa85
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939275"
---
# <a name="debug-r-in-visual-studio"></a>Eseguire il debug di R in Visual Studio

Strumenti R per Visual Studio (RTVS) si integra con l'esperienza di debug completa di Visual Studio (vedere [Debugging in Visual Studio](/visualstudio/debugger/debugger-feature-tour) (Debug in Visual Studio). Questo supporto include punti di interruzione, collegamento a processi in esecuzione, esame e controllo delle variabili ed esame dello stack di chiamate. In questo articolo vengono quindi esaminati gli aspetti del debug che sono univoci per R e RTVS.

Avviare il debugger per il file di avvio R in un progetto R è un'operazione identica a quella per altri tipi di progetto: usare **Debug** > **Avvia debug**, **F5** o il **file di avvio di origine** nella barra degli strumenti di debug:

![Pulsante di avvio del debugger per R](media/debugger-start-button.png)

Per modificare il file di avvio, fare clic con il pulsante destro del mouse su un file in Esplora soluzioni e selezionare **Imposta come script R di avvio**.

In tutti i casi, il debug "dà origine" al file nella finestra interattiva, ovvero lo carica e lo esegue da qui, come illustrato dall'output della finestra interattiva:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Si noti che come origine dello script viene usata la funzione `rtvs::debug_source`. Questa funzione è obbligatoria, perché RTVS deve modificare il codice in preparazione al debug. Quando si usa un comando di sourcing RTVS e un debugger è collegato, Visual Studio usa automaticamente `rtvs::debug_source`.

È anche possibile collegare in modo manuale il debugger direttamente dalla finestra interattiva usando il comando **R Tools** > **Sessione** > **Collega debugger**, il comando **Debug** > **Collega a R interattivo** o il comando **Collega debugger** nella barra degli strumenti della finestra interattiva. Dopo avere eseguito questa operazione, è responsabilità dell'utente eseguire il sourcing dei file di cui vuole eseguire il debug. Se si vuole eseguire manualmente il sourcing dei file, assicurarsi di usare `rtvs::debug_source` e non il comando `source` normale in R.

Questa connessione tra il debugger e la finestra interattiva semplifica alcune operazioni, come ad esempio la chiamata e il debugging di una funzione con valori di parametro diversi. Ad esempio, si supponga di avere la funzione seguente in un file originato, ovvero caricato nella sessione:

```R
add <- function(x, y) {
    return(x + y)
}
```

Impostare quindi un punto di interruzione nell'istruzione `return`. A questo punto, se nella finestra interattiva si immette `add(4,5)`, il debugger si interrompe sul punto di interruzione.

## <a name="environment-browser-in-the-interactive-window"></a>Browser ambiente nella finestra interattiva

Quando il debugger si arresta, viene arrestato anche il prompt del browser di ambiente nella [finestra interattiva](interactive-repl-for-r-in-visual-studio.md). Il prompt viene visualizzata come `Browse[n]>` dove n è un numero.

Il browser ambiente supporta un numero di comandi speciali:

| Comando | Description |
| --- | --- |
| n | next: esegue l'istruzione successiva nel file di codice (uguale a step over). |
| s | step into: esegue l'istruzione successiva nel file di codice, passando all'ambito della funzione se l'istruzione successiva è una chiamata di funzione. |
| f | finish: esegue il resto dell'ambito della funzione corrente e restituisce al chiamante (uguale a step out). |
| c, cont | continue: esegue il programma fino al punto di interruzione successivo. |
| Q | quits: termina la sessione di debug. |
| dove | show stack: consente di visualizzare lo stack di chiamate nella finestra interattiva. |
| guida | show help: consente di visualizzare le chiamate disponibili nella finestra interattiva. |
| &lt;expr&gt; | valuta l'espressione in *expr*. |

![Browser ambiente nella finestra interattiva](media/debugger-environment-browser.png)
