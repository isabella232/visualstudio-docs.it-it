---
title: Debug di applicazioni multithreading | Microsoft Docs
ms.custom: seodec18
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07710ed0188baf48a567bb3c003f174814c30094
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "53907891"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debug di applicazioni multithreading in Visual Studio
Un thread è una sequenza di istruzioni a cui il sistema operativo concede il tempo del processore. Ogni processo in esecuzione nel sistema operativo è composto da almeno un thread. I processi composti da più di un thread sono detti multithreading.  
  
Computer con più processori, processori multicore o i processi hyperthreading sono eseguibili diversi thread simultanei. Elaborazione parallela con molti thread può migliorare notevolmente le prestazioni del programma, ma può anche semplificare il debug più difficile perché si vuole monitorare molti thread.  
  
Il multithreading può introdurre nuovi tipi di potenziali bug. Ad esempio, due o più thread potrebbe essere necessario accedere alla risorsa stessa, ma un solo thread alla volta può accedere in modo sicuro alla risorsa. Qualche forma di esclusione reciproca è necessario assicurarsi che solo un thread è l'accesso alla risorsa in qualsiasi momento. Se l'esclusione reciproca viene implementato in modo non corretto, è possibile creare un *deadlock* condizione in cui non verrà eseguito alcun thread. I deadlock sono spesso un problema difficile eseguire il debug.

## <a name="tools-for-debugging-multithreaded-apps"></a>Strumenti per il debug di applicazioni multithreading

Visual Studio offre diversi strumenti per eseguire il debug di applicazioni a thread multipli.

- Per i thread sono i principali strumenti per il debug dei thread di **thread** (finestra), i marcatori dei thread nelle finestre di origine, il **stack in parallelo** finestra, il **espressioni di controllo parallela** finestra e il **posizione di Debug** sulla barra degli strumenti. Per apprendere le **thread** finestra e **posizione di Debug** sulla barra degli strumenti, vedere [procedura dettagliata: Eseguire il debug con la finestra Thread](../debugger/how-to-use-the-threads-window.md). Per informazioni su come usare il **stack in parallelo** e **espressioni di controllo parallela** windows, vedere [iniziare il debug di un'applicazione multithreading](../debugger/get-started-debugging-multithreaded-apps.md). Entrambi gli argomenti illustrano come usare i marcatori dei thread.
  
- Per il codice che usa il [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) o il [Runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime/), sono i principali strumenti per eseguire il debug di **stack in parallelo** (finestra), il **Espressioni di controllo parallela** finestra e il **attività** finestra, che supporta anche JavaScript. Per iniziare, vedere [procedura dettagliata: Debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md) e [procedura dettagliata: Debug di un'applicazione C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application). 

- Per il debug dei thread nella GPU, lo strumento principale è il **thread GPU** finestra. Vedere [Procedura: Usare la finestra Thread GPU](../debugger/how-to-use-the-gpu-threads-window.md).  

- Per i processi, sono i principali strumenti di **Connetti a processo** nella finestra di dialogo il **processi** finestra e il **posizione di Debug** sulla barra degli strumenti.  
  
Visual Studio offre anche potenti punti di interruzione e punti di analisi, che può essere utile quando si esegue il debug di applicazioni multithreading. Usare condizioni punto di interruzione e i filtri per posizionare i punti di interruzione nei singoli thread. I punti di analisi consentono di tracciare l'esecuzione del programma senza violare, per analizzare i problemi quali i deadlock. Per altre informazioni, vedere [azioni di punto di interruzione e punti di analisi](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Il debug di un'applicazione multithreading dotata di un'interfaccia utente può essere particolarmente complesso. È possibile eseguire l'applicazione in un secondo computer e il debug remoto. Per altre informazioni, vedere [debug remoto](../debugger/remote-debugging.md).  
  
## <a name="articles-about-debugging-multithreaded-apps"></a>Articoli sul debug di applicazioni multithreading

 [Iniziare il debug di un'applicazione multithreading](../debugger/get-started-debugging-multithreaded-apps.md)   
 Panoramica delle funzionalità, che mettono in evidenza le funzionalità di debug dei thread di **stack in parallelo** finestra e il **espressioni di controllo parallela** finestra.

 [Strumenti per il debug di thread e processi](../debugger/debug-threads-and-processes.md)  
 Elenca le funzionalità degli strumenti per il debug di thread e processi.  
  
 [Eseguire il debug di più processi](../debugger/debug-multiple-processes.md)  
 Spiega la procedura per eseguire il debug di più processi

 [Procedura dettagliata: Eseguire il debug con la finestra Thread](../debugger/how-to-use-the-threads-window.md).  
 Procedura dettagliata che illustra come usare il **thread** finestra e il **posizione di Debug** sulla barra degli strumenti. 

 [Procedura dettagliata: Debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Procedura dettagliata che illustra come usare il **stack in parallelo** e **attività** windows.  
  
 [Procedura: Passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Diversi modi per cambiare il contesto di debug a un altro thread.  
  
 [Procedura: Impostare e rimuovere i flag dei thread](../debugger/how-to-flag-and-unflag-threads.md)  
 Aggiunta di contrassegni o flag ai thread a cui è opportuno prestare particolare attenzione durante il debug.    
  
 [Procedura: Eseguire il debug su un cluster a prestazioni elevate](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Tecniche per il debug di applicazioni in esecuzione su un cluster ad alte prestazioni.  

 [Suggerimenti per il debug dei thread in codice nativo](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Semplici tecniche utili per il debug di thread nativi. 

 [Procedura: Impostare il nome di un thread in codice nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Attribuzione di un nome da visualizzare nella finestra **Thread**.  
  
 [Procedura: Impostare il nome di un thread in codice gestito](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Attribuzione di un nome da visualizzare nella finestra **Thread**. 
  
## <a name="see-also"></a>Vedere anche  

[Usare i punti di interruzione](../debugger/using-breakpoints.md)  
[Threading](/dotnet/standard/threading/index)  
[Multithreading nei componenti](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
[Supporto del multithreading per il codice precedente (Visual C++)](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)  
 [Debug di thread e processi](../debugger/debug-threads-and-processes.md)   
 [Debug remoto](../debugger/remote-debugging.md)