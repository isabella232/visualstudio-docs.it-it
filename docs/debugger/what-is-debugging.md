---
title: Che cos'è il debug?
description: Informazioni sul modo in cui si intende eseguire il debug di un'app
ms.custom: debug-experiment
ms.date: 10/17/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c01317f3b8fa92cf1bc17c3745f708e0d3f26e5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62901226"
---
# <a name="what-is-debugging"></a>Che cos'è il debug?

Il debugger di Visual Studio è uno strumento potente. Prima di illustrare il modo in cui usarlo, è necessario parlare di alcuni termini, ad esempio il *debugger*, il *debug*e la *modalità di debug*. In questo modo, quando si parlerà più avanti sull'individuazione e la correzione dei bug, si parlerà della stessa cosa.

## <a name="debugger-vs-debugging"></a>Confronto tra debugger e debug

Il termine *debug* può significare un numero elevato di elementi diversi, ma in genere significa rimuovere i bug dal codice. A questo punto, è possibile eseguire questa operazione in molti modi. Ad esempio, è possibile eseguire il debug analizzando il codice cercando errori di digitazione o usando un analizzatore di codice. È possibile eseguire il debug del codice usando un profiler delle prestazioni. In alternativa, è possibile eseguire il debug utilizzando un *debugger*.

Un debugger è uno strumento di sviluppo molto specializzato che si connette all'app in esecuzione e consente di ispezionare il codice. Nella documentazione di debug di Visual Studio, si tratta in genere di ciò che si intende fare quando si dice "debug".

## <a name="debug-mode-vs-running-your-app"></a>Modalità di debug rispetto all'esecuzione dell'app

Quando si esegue l'app in Visual Studio per la prima volta, è possibile avviarla premendo il pulsante freccia verde ![Avvia debug](../debugger/media/dbg-tour-start-debugging.png "Avvia debug") sulla barra degli strumenti (o **F5**). Per impostazione predefinita, il valore di **debug** viene visualizzato nell'elenco a discesa a sinistra. Se non si ha familiarità con Visual Studio, questo può comportare l'impressione che il debug dell'app abbia qualcosa a che fare con l'esecuzione dell'app, ma si tratta fondamentalmente di due attività molto diverse.

![Selezionare una compilazione di debug](../debugger/media/what-is-debugging-debug-build.png)

Un valore di **debug** indica una configurazione di debug. Quando si avvia l'app (premere la freccia verde o **F5**) in una configurazione di debug, l'app viene avviata in *modalità di debug*, il che significa che è in esecuzione l'app con un debugger collegato. Questo consente un set completo di funzionalità di debug che è possibile usare per individuare i bug nell'app.

Se è aperto un progetto, scegliere il selettore a discesa in cui è indicato **debug** e scegliere **Release** .

![Selezionare una build di rilascio](../debugger/media/what-is-debugging-release-build.png)

Quando si passa a questa impostazione, il progetto viene modificato da una configurazione di debug a una configurazione di rilascio. Progetti di Visual Studio installata versione separata e configurazioni per il programma di debug. Compilare la versione di debug per il debug e la versione di rilascio per la distribuzione finale della versione. Una build di rilascio è ottimizzata per le prestazioni, ma una compilazione di debug è migliore per il debug.

## <a name="when-to-use-a-debugger"></a>Quando usare un debugger

Il debugger è uno strumento essenziale per individuare e correggere i bug nelle app. Tuttavia, il contesto è King ed è importante sfruttare tutti gli strumenti disponibili per eliminare rapidamente i bug o gli errori. A volte, il giusto "strumento" potrebbe essere una migliore procedura di codifica. Imparando a usare il debugger rispetto a un altro strumento, si apprenderà anche come usare il debugger in modo più efficace.

## <a name="next-steps"></a>Passaggi successivi

In questo articolo si sono appresi alcuni concetti di debug generali. Successivamente, è possibile iniziare a imparare a eseguire il debug con Visual Studio e come scrivere codice con meno bug. Gli articoli seguenti illustrano gli esempi di codice C#, ma i concetti si applicano a tutti i linguaggi supportati da Visual Studio.

> [!div class="nextstepaction"]
> [Debug per principianti](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [Tecniche e strumenti di debug CRT](../debugger/write-better-code-with-visual-studio.md)
