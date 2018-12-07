---
title: Che cos'è il debug?
description: Comprendere che cosa significa eseguire il debug di un'app
ms.custom: debug-experiments
ms.date: 10/17/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f0aa6cbe09f902ef69e1fd5cb3a2d9712cabf28
ms.sourcegitcommit: d7f232a7596420e40ff8051d42cdf90203af4a74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2018
ms.locfileid: "52821448"
---
# <a name="what-is-debugging"></a>Che cos'è il debug?

Il debugger di Visual Studio è uno strumento potente. Prima di illustrare come usarlo, vogliamo parlare di alcuni termini, ad esempio *debugger*, *debug*, e *modalità di debug*. In questo modo, quando si parla in un secondo momento trovando e correggendo i bug, abbiamo parlerò la stessa cosa.

## <a name="debugger-vs-debugging"></a>Debugger e debug

Il termine *debug* può significare numerose operazioni diverse, ma più letteralmente, significa rimuovere i bug dal codice. A questo punto, esistono molti modi per eseguire questa operazione. Ad esempio, potrebbe eseguire il debug eseguendo la scansione del codice alla ricerca di errori di digitazione o utilizzando un analizzatore del codice. Si potrebbe eseguire il debug di codice tramite un profiler delle prestazioni. In alternativa, è possibile eseguire il debug usando un *debugger*.

Un debugger è uno strumento molto specializzata per gli sviluppatori che collega all'App in esecuzione e consente di esaminare il codice. Nella documentazione di debug per Visual Studio, si tratta in genere cosa intendiamo Quando parliamo di "debug".

## <a name="debug-mode-vs-running-your-app"></a>Eseguire il debug in modalità e con esecuzione dell'app

Quando si esegue l'app in Visual Studio per la prima volta, è possibile avviarlo facendo clic sul pulsante freccia verde ![Avvia debug](../debugger/media/dbg-tour-start-debugging.png "Avvia debug") sulla barra degli strumenti (o **F5**). Per impostazione predefinita, il **Debug** valore verrà visualizzato nell'elenco a discesa a sinistra. Se si ha familiarità con Visual Studio, questo può rendere l'impressione che debug della tua app con operazioni da eseguire con l'esecuzione all'applicazione, cui si esegue, ma fondamentalmente si tratta di due attività molto diverse.

![Selezionare una build di Debug](../debugger/media/what-is-debugging-debug-build.png)

Oggetto **Debug** valore indica una configurazione di debug. Quando si avvia l'app (premere la freccia verde o **F5**) in una configurazione di debug, avviare l'app *modalità di debug*, vale a dire si esegue l'app con un debugger collegato. In questo modo un set completo di funzionalità che è possibile usare per individuare i bug nell'app di debug.

Se è aperto un progetto, scegliere il selettore di elenco a discesa in cui viene indicato **Debug** e scegliere **rilascio** invece.

![Selezionare una build di rilascio](../debugger/media/what-is-debugging-release-build.png)

Quando si cambia questa impostazione, si modifica il progetto da una configurazione di debug per una configurazione di rilascio. Progetti di Visual Studio installata versione separata e configurazioni per il programma di debug. Si compila la versione di debug per il debug e la versione di rilascio per la distribuzione finale. Una build di rilascio è ottimizzata per le prestazioni, ma è preferibile per il debug di una build di debug.

## <a name="when-to-use-a-debugger"></a>Quando usare un debugger

Il debugger è uno strumento essenziale per trovare e correggere i bug nelle app. Tuttavia, contesto è king ed è importante sfruttare tutti gli strumenti all'elemento eliminabile che consentono di eliminare rapidamente i bug o errori. In alcuni casi, il diritto "strumento" potrebbe essere una procedura di codifica meglio. Da quando l'utilizzo del debugger e un altro strumento di apprendimento, si apprenderà anche come usare il debugger in modo più efficace. Se si conosce già, è necessario conoscere il debugger, vedere [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md). In caso contrario, fare clic sul collegamento nella **passaggi successivi**.

## <a name="next-steps"></a>Passaggi successivi

In questo articolo si sono appresi alcuni concetti di debug generali. Successivamente, è possibile iniziare a imparare come eseguire il debug con Visual Studio e spiega come scrivere codice con meno bug. L'articolo seguente illustra C# esempi di codice, ma i concetti si applicano a tutte le lingue supportate da Visual Studio.

> [!div class="nextstepaction"]
> [Correggere i bug scrivendo codice C# migliore](../debugger/write-better-code-with-visual-studio.md)