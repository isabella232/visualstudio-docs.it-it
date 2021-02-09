---
title: Eseguire il debug di applicazioni multithread | Microsoft Docs
description: Eseguire il debug di applicazioni multithreading in Visual Studio. Esaminare gli strumenti e altri articoli sul debug di app multithread.
ms.custom: SEO-VS-2020, seodec18
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
ms.workload:
- multiple
ms.openlocfilehash: e7a133b4b59b11525a7f7ba776b3b4a4a1e6a31e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873210"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debug di applicazioni multithreading in Visual Studio
Un thread è una sequenza di istruzioni a cui il sistema operativo concede tempo di elaborazione. Ogni processo in esecuzione nel sistema operativo è composto da almeno un thread. I processi composti da più di un thread sono detti multithreading.

I computer con più processori, processori multicore o processi di hyperthreading possono eseguire più thread simultaneamente. L'elaborazione parallela tramite molti thread può migliorare significativamente le prestazioni del programma, ma può anche rendere più difficile il debug perché si sta monitorando molti thread.

Il multithreading può introdurre nuovi tipi di bug potenziali. Ad esempio, due o più thread potrebbero dover accedere alla stessa risorsa, ma un solo thread alla volta può accedere in modo sicuro alla risorsa. È necessaria una forma di esclusione reciproca per assicurarsi che un solo thread acceda alla risorsa in qualsiasi momento. Se l'esclusione reciproca viene implementata in modo errato, è possibile creare una condizione di *deadlock* in cui non verrà eseguito alcun thread. I deadlock rappresentano spesso un problema difficile da eseguire per il debug.

## <a name="tools-for-debugging-multithreaded-apps"></a>Strumenti per il debug di app multithread

Visual Studio offre diversi strumenti da usare per il debug di app multithread.

- Per i thread, gli strumenti principali per il debug dei thread sono la finestra **thread** , i marcatori dei thread nelle finestre di origine, la finestra **stack in parallelo** , la finestra espressione di **controllo in parallelo** e la barra degli strumenti posizione di **debug** . Per ulteriori informazioni sulla finestra **thread** e sulla barra degli strumenti **posizione di debug** , vedere [procedura dettagliata: eseguire il debug utilizzando la finestra thread](../debugger/how-to-use-the-threads-window.md). Per informazioni su come usare le finestre **stack in parallelo** e espressioni di controllo in **parallelo** , vedere [Introduzione al debug di un'applicazione multithreading](../debugger/get-started-debugging-multithreaded-apps.md). Entrambi gli argomenti illustrano come usare i marcatori di thread.

- Per il codice che usa il [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) o il [runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime/), gli strumenti principali per il debug sono la finestra **stack in parallelo** , la finestra espressioni di controllo in **parallelo** e la finestra **attività** , che supporta anche JavaScript. Per iniziare, vedere [procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md) e [procedura dettagliata: debug di un'applicazione C++ amp](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application).

- Per il debug dei thread sulla GPU, lo strumento principale è la finestra **thread GPU** . Vedere [procedura: usare la finestra thread GPU](../debugger/how-to-use-the-gpu-threads-window.md).

- Per i processi, gli strumenti principali sono la finestra **di dialogo Connetti a processo** , la finestra **processi** e la barra degli strumenti **posizione di debug** .

Visual Studio offre anche potenti punti di interruzione e punti, che possono essere utili quando si esegue il debug di applicazioni multithread. Utilizzare le condizioni e i filtri dei punti di interruzione per inserire punti di interruzione nei singoli thread. Punti consentono di tracciare l'esecuzione del programma senza interruzioni, per studiare problemi quali i deadlock. Per ulteriori informazioni, vedere azioni del punto di [interruzione e punti](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Il debug di un'applicazione multithreading dotata di un'interfaccia utente può essere particolarmente complesso. È consigliabile eseguire l'applicazione in un secondo computer e utilizzare il debug remoto. Per ulteriori informazioni, vedere [Remote Debugging](../debugger/remote-debugging.md).

## <a name="articles-about-debugging-multithreaded-apps"></a>Articoli sul debug di app multithread

 [Introduzione al debug di un'applicazione multithreading](../debugger/get-started-debugging-multithreaded-apps.md)

Panoramica delle funzionalità di debug dei thread, evidenziando le funzionalità della finestra **stack in parallelo** e della finestra espressione di **controllo in parallelo** .

 [Strumenti per il debug di thread e processi](../debugger/debug-threads-and-processes.md)

Elenca le funzionalità degli strumenti per il debug di thread e processi.

 [Eseguire il debug di più processi](../debugger/debug-multiple-processes.md)

Spiega la procedura per eseguire il debug di più processi

 [Procedura dettagliata: eseguire il debug utilizzando la finestra thread](../debugger/how-to-use-the-threads-window.md).

Procedura dettagliata in cui viene illustrato come utilizzare la finestra **thread** e la barra degli strumenti **posizione di debug** .

 [Procedura dettagliata: Eseguire il debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)

Procedura dettagliata che illustra come utilizzare le finestre **stack in parallelo** e **attività** .

 [Procedura: Passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)

Diversi modi per passare il contesto di debug a un altro thread.

 [Procedura: Impostare e rimuovere i flag dei thread](../debugger/how-to-flag-and-unflag-threads.md)

Aggiunta di contrassegni o flag ai thread a cui è opportuno prestare particolare attenzione durante il debug.

 [Procedura: eseguire il debug in un cluster ad alte prestazioni](../debugger/how-to-debug-on-a-high-performance-cluster.md)

Tecniche per il debug di applicazioni in esecuzione su un cluster ad alte prestazioni.

 [Suggerimenti per il debug dei thread in codice nativo](../debugger/tips-for-debugging-threads-in-native-code.md)

Semplici tecniche utili per il debug di thread nativi.

 [Procedura: Impostare il nome di un thread in codice nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)

Attribuzione di un nome da visualizzare nella finestra **Thread**.

 [Procedura: impostare il nome di un thread nel codice gestito](../debugger/how-to-set-a-thread-name-in-managed-code.md)

Attribuzione di un nome da visualizzare nella finestra **Thread**.

## <a name="see-also"></a>Vedi anche

- [Usare i punti di interruzione](../debugger/using-breakpoints.md)
- [Threading](/dotnet/standard/threading/index)
- [Multithreading nei componenti](/previous-versions/3es4b6yy(v=vs.140))
- [Supporto del multithreading per il codice precedente](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [Debug di thread e processi](../debugger/debug-threads-and-processes.md)
- [Debug remoto](../debugger/remote-debugging.md)