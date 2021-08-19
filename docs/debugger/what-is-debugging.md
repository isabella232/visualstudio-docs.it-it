---
title: Che cos'è il debug?
description: Comprendere cosa significa eseguire il debug di un'app
ms.custom: debug-experiment
ms.date: 10/17/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4b2303480e242585801f8908f544df6409699d18
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146576"
---
# <a name="what-is-debugging"></a>Che cos'è il debug?

Il debugger Visual Studio è uno strumento potente. Prima di illustrare come usarlo, è necessario parlare di alcuni termini, ad esempio *debugger,* *debug* e *modalità di debug.* In questo modo, quando in seguito si parlerà della ricerca e della correzione dei bug, si parlerà della stessa cosa.

## <a name="debugger-vs-debugging"></a>Confronto tra debugger e debug

Il termine *debug* può significare molti elementi diversi, ma più letteralmente significa rimuovere i bug dal codice. A questo punto, esistono molti modi per eseguire questa operazione. Ad esempio, è possibile eseguire il debug eseguendo l'analisi del codice alla ricerca di errori di digitazione o usando un analizzatore del codice. È possibile eseguire il debug del codice usando un profiler delle prestazioni. In caso contrario, è possibile eseguire il debug usando un *debugger*.

Un debugger è uno strumento di sviluppo molto specializzato che si collega all'app in esecuzione e consente di esaminare il codice. Nella documentazione di debug per Visual Studio, questo è in genere ciò che si intende quando si dice "debug".

## <a name="debug-mode-vs-running-your-app"></a>Modalità di debug e esecuzione dell'app

Quando si esegue l'app in Visual Studio per la prima volta, è possibile avviarla premendo il pulsante freccia verde ![Avvia](../debugger/media/dbg-tour-start-debugging.png "Avvia debug") debug sulla barra degli strumenti (o **F5).** Per impostazione predefinita, **il valore Debug** viene visualizzato nell'elenco a discesa a sinistra. Se non si ha la Visual Studio, si può lasciare l'impressione che il debug dell'app abbia a che fare con l'esecuzione dell'app, ma si tratta fondamentalmente di due attività molto diverse.

![Selezionare una build di debug](../debugger/media/what-is-debugging-debug-build.png)

Un **valore Debug** indica una configurazione di debug. Quando si avvia l'app (premere la freccia verde o **F5)** in una configurazione di debug, si avvia l'app in modalità *di debug,* ovvero l'app viene eseguita con un debugger collegato. In questo modo è possibile abilitare un set completo di funzionalità di debug che è possibile usare per individuare i bug nell'app.

Se è aperto un progetto, scegliere il selettore a discesa in cui è **debug** e scegliere **invece Versione.**

![Selezionare una build di versione](../debugger/media/what-is-debugging-release-build.png)

Quando si passa a questa impostazione, si modifica il progetto da una configurazione di debug a una configurazione di rilascio. Progetti di Visual Studio installata versione separata e configurazioni per il programma di debug. Compilare la versione di debug per il debug e la versione di rilascio per la distribuzione finale della versione. Una build di rilascio è ottimizzata per le prestazioni, ma una build di debug è migliore per il debug.

## <a name="when-to-use-a-debugger"></a>Quando usare un debugger

Il debugger è uno strumento essenziale per trovare e correggere i bug nelle app. Tuttavia, il contesto è re ed è importante sfruttare tutti gli strumenti disponibili per eliminare rapidamente bug o errori. In alcuni casi, lo "strumento" giusto potrebbe essere una procedura di scrittura del codice migliore. Apprendendo quando usare il debugger e altri strumenti, si apprenderà anche come usare il debugger in modo più efficace.

## <a name="next-steps"></a>Passaggi successivi

In questo articolo si sono appresi alcuni concetti di debug generali. Successivamente, è possibile iniziare a imparare a eseguire il debug con Visual Studio e come scrivere codice con meno bug. Gli articoli seguenti illustrano esempi di codice C#, ma i concetti si applicano a tutti i linguaggi supportati da Visual Studio.

> [!div class="nextstepaction"]
> [Debug per principianti](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [Tecniche e strumenti di debug CRT](../debugger/write-better-code-with-visual-studio.md)
