---
title: Eseguire il debug di applicazioni multithreading | Microsoft Docs
description: Eseguire il debug di applicazioni multithreading in Visual Studio. Esaminare gli strumenti e altri articoli sul debug di app multithreading.
ms.custom: SEO-VS-2020
ms.date: 11/06/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6a3c3b20117061f06d7f5e65e1cd9ec4fbd0b814
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626544"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debug di applicazioni multithreading in Visual Studio
Un thread è una sequenza di istruzioni a cui il sistema operativo concede il tempo del processore. Ogni processo in esecuzione nel sistema operativo è composto da almeno un thread. I processi composti da più di un thread sono detti multithreading.

I computer con più processori, processori multi-core o processi di hyperthreading possono eseguire più thread simultanei. L'elaborazione parallela che usa molti thread può migliorare notevolmente le prestazioni del programma, ma può anche rendere più difficile il debug perché si stanno verificando molti thread.

Il multithreading può introdurre nuovi tipi di bug potenziali. Ad esempio, due o più thread potrebbero dover accedere alla stessa risorsa, ma solo un thread alla volta può accedere in modo sicuro alla risorsa. Una qualche forma di esclusione reciproca è necessaria per assicurarsi che un solo thread accedono alla risorsa in qualsiasi momento. Se l'esclusione reciproca viene implementata in modo non corretto, può creare una *condizione di deadlock* in cui non verrà eseguito alcun thread. I deadlock sono spesso un problema difficile da eseguire il debug.

## <a name="tools-for-debugging-multithreaded-apps"></a>Strumenti per il debug di app multithreading

Visual Studio strumenti diversi per l'uso nel debug di app multithreading.

- Per i thread, gli strumenti  principali per il debug dei thread sono la finestra  Thread, i marcatori di thread nelle finestre di origine, la finestra **Stack** in parallelo, la finestra Espressioni di controllo in parallelo e la barra degli strumenti **Posizione di** debug. Per informazioni sulla finestra **Thread e** sulla barra degli strumenti Percorso **di debug,** vedere [Procedura dettagliata: Eseguire il debug usando la finestra Thread](../debugger/how-to-use-the-threads-window.md). Per informazioni su come usare le finestre **Stack in** parallelo e **Controllo** parallelo, vedere Introduzione al debug di [un'applicazione multithreading](../debugger/get-started-debugging-multithreaded-apps.md). Entrambi gli argomenti illustrano come usare i marcatori di thread.

- Per il codice che usa Task Parallel Library [(TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) o [runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime/), gli strumenti principali per il  debug sono la  finestra **Stack** paralleli, la finestra Espressioni di controllo in parallelo e la finestra Attività , che supporta anche JavaScript. Per iniziare, vedere [Procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md) e Procedura dettagliata: debug di [un C++ AMP app.](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)

- Per il debug dei thread nella GPU, lo strumento principale è la **finestra Thread GPU.** Vedere [Procedura: Usare la finestra Thread GPU](../debugger/how-to-use-the-gpu-threads-window.md).

- Per i processi, gli strumenti principali sono la **finestra** di dialogo Collega a processo, la **finestra** Processi e la barra degli **strumenti Percorso di** debug.

Visual Studio fornisce anche potenti punti di interruzione e punti di traccia, che possono essere utili quando si esegue il debug di applicazioni multithreading. Usare le condizioni e i filtri dei punti di interruzione per posizionare i punti di interruzione nei singoli thread. I punti di traccia consentono di tracciare l'esecuzione del programma senza interruzione, per studiare problemi come i deadlock. Per altre informazioni, vedere [Azioni dei punti di interruzione e punti di traccia](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Il debug di un'applicazione multithreading dotata di un'interfaccia utente può essere particolarmente complesso. È possibile eseguire l'applicazione in un secondo computer e usare il debug remoto. Per altre informazioni, vedere [Debug remoto.](../debugger/remote-debugging.md)

## <a name="articles-about-debugging-multithreaded-apps"></a>Articoli sul debug di app multithreading

 [Introduzione al debug di un'applicazione multithreading](../debugger/get-started-debugging-multithreaded-apps.md)

Presentazione delle funzionalità di debug dei thread, che sottolineano le funzionalità nella finestra **Stack** in parallelo e nella **finestra Espressioni di controllo** in parallelo.

 [Strumenti per il debug di thread e processi](../debugger/debug-threads-and-processes.md)

Elenca le funzionalità degli strumenti per il debug di thread e processi.

 [Eseguire il debug di più processi](../debugger/debug-multiple-processes.md)

Spiega la procedura per eseguire il debug di più processi

 [Procedura dettagliata: Eseguire il debug usando la finestra Thread](../debugger/how-to-use-the-threads-window.md).

Procedura dettagliata che illustra come usare la finestra **Thread** e la barra degli **strumenti Percorso di** debug.

 [Procedura dettagliata: Eseguire il debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)

Procedura dettagliata che illustra come usare le **finestre Stack e** Attività in parallelo. 

 [Procedura: Passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)

Diversi modi per passare il contesto di debug a un altro thread.

 [Procedura: Impostare e rimuovere i flag dei thread](../debugger/how-to-flag-and-unflag-threads.md)

Aggiunta di contrassegni o flag ai thread a cui è opportuno prestare particolare attenzione durante il debug.

 [Procedura: Eseguire il debug in un cluster ad alte prestazioni](../debugger/how-to-debug-on-a-high-performance-cluster.md)

Tecniche per il debug di applicazioni in esecuzione su un cluster ad alte prestazioni.

 [Suggerimenti per il debug dei thread in codice nativo](../debugger/tips-for-debugging-threads-in-native-code.md)

Semplici tecniche utili per il debug di thread nativi.

 [Procedura: Impostare il nome di un thread in codice nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)

Attribuzione di un nome da visualizzare nella finestra **Thread**.

 [Procedura: Impostare un nome di thread nel codice gestito](../debugger/how-to-set-a-thread-name-in-managed-code.md)

Attribuzione di un nome da visualizzare nella finestra **Thread**.

## <a name="see-also"></a>Vedi anche

- [Usare i punti di interruzione](../debugger/using-breakpoints.md)
- [Threading](/dotnet/standard/threading/index)
- [Multithreading nei componenti](/previous-versions/3es4b6yy(v=vs.140))
- [Supporto del multithreading per il codice precedente](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [Debug di thread e processi](../debugger/debug-threads-and-processes.md)
- [Debug remoto](../debugger/remote-debugging.md)