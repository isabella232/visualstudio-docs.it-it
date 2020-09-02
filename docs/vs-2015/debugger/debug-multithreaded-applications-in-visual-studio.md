---
title: Debug di applicazioni multithreading
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cb43c9a32f3dfd0a6383d466f7cd283acf0ab3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691272"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debug di applicazioni multithreading in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un thread è una sequenza di istruzioni in base alla quale il sistema operativo esegue l'allocazione del tempo processore. Ogni processo in esecuzione nel sistema operativo è composto da almeno un thread. I processi composti da più di un thread sono detti multithreading.

 I computer multiprocessore, i processori multicore e i processi hyperthreading sono in grado di eseguire contemporaneamente più thread. Se da un lato l'elaborazione parallela di più thread può migliorare notevolmente le prestazioni dei programmi, dall'altro può rendere il debug più difficoltoso poiché introduce la necessità di tenere traccia di più thread.

 Il multithreading introduce inoltre nuovi tipi di possibili bug. Accade spesso, ad esempio, che due o più thread debbano accedere alla stessa risorsa, alla quale però può accedere un solo thread alla volta. Deve necessariamente esistere una qualche forma di esclusione reciproca per garantire l'accesso alla risorsa di un solo thread alla volta. Se l'esclusione reciproca viene eseguita in modo non corretto, è possibile creare una condizione di *deadlock* in cui non è possibile eseguire alcun thread. I deadlock possono rappresentare un problema particolarmente difficile da risolvere con il debug.

 Visual Studio fornisce una finestra **thread** , una finestra thread GPU, una finestra espressioni di controllo parallela e altre funzionalità che semplificano il debug multithreading. Il modo migliore per acquisire ulteriori informazioni sulle nuove funzionalità dell'interfaccia di threading consiste nell'eseguire le procedure dettagliate. Vedere [procedura dettagliata: debug di un'applicazione multithreading](../debugger/walkthrough-debugging-a-multithreaded-application.md) e [procedura dettagliata: debug di un'applicazione C++ amp](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).

 Visual Studio offre anche potenti punti di interruzione e punti di analisi che possono rivelarsi molto utili per il debug di applicazioni multithreading. È possibile applicare filtri dei punti di interruzione per inserire punti di interruzione in corrispondenza di singoli thread. Vedere [utilizzo](../debugger/using-breakpoints.md) di punti di interruzione

 Il debug di un'applicazione multithreading dotata di un'interfaccia utente può essere particolarmente complesso. In tal caso, potrebbe essere necessario eseguire l'applicazione in un secondo computer e utilizzare il debug remoto. Per informazioni, vedere [Remote Debugging](../debugger/remote-debugging.md).

## <a name="in-this-section"></a>Contenuto della sezione
 [Debug di thread e processi](../debugger/debug-threads-and-processes.md) Illustra le nozioni di base per il debug di thread e processi.

 [Debug di più processi](../debugger/debug-multiple-processes.md) Viene illustrato come eseguire il debug di più processi.

 [Procedura: usare la finestra thread](../debugger/how-to-use-the-threads-window.md) Procedure utili per il debug dei thread con la finestra **thread** .

 [Procedura: passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md) Tre modi per passare il contesto di debug a un altro thread.

 [Procedura: contrassegnare e decontrassegnare i thread](../debugger/how-to-flag-and-unflag-threads.md) Contrassegnare o contrassegnare i thread a cui si desidera prestare particolare attenzione durante il debug.

 [Procedura: impostare il nome di un thread in codice nativo](../debugger/how-to-set-a-thread-name-in-native-code.md) Assegnare al thread un nome da visualizzare nella finestra **thread** .

 [Procedura: impostare il nome di un thread nel codice gestito](../debugger/how-to-set-a-thread-name-in-managed-code.md) Assegnare al thread un nome da visualizzare nella finestra **thread** .

 [Procedura dettagliata: debug di un'applicazione multithreading](../debugger/walkthrough-debugging-a-multithreaded-application.md).
Presentazione guidata delle funzionalità di debug dei thread, con particolare attenzione alle funzionalità procedura [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].

 [Procedura: eseguire il debug in un cluster ad alte prestazioni](../debugger/how-to-debug-on-a-high-performance-cluster.md) Tecniche per il debug di un'applicazione in esecuzione in un cluster ad alte prestazioni.

 [Suggerimenti per il debug dei thread in codice nativo](../debugger/tips-for-debugging-threads-in-native-code.md) Tecniche semplici che possono essere utili per il debug di thread nativi.

 [Uso della finestra attività](../debugger/using-the-tasks-window.md) Mostra un elenco di tutti gli oggetti attività gestiti o nativi, inclusi lo stato e altre informazioni utili.

 [Uso della finestra stack in parallelo](../debugger/using-the-parallel-stacks-window.md) Mostra gli stack di chiamate di più thread (o attività) in un'unica visualizzazione e unisce anche segmenti dello stack comuni tra i thread (o attività).

 [Procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md) Procedura dettagliata che illustra come utilizzare le finestre attività in parallelo e stack in parallelo.

 [Procedura: usare la finestra espressione di controllo in parallelo](../debugger/how-to-use-the-parallel-watch-window.md) Controllare i valori e le espressioni in più thread.

 [Procedura: usare la finestra thread GPU](../debugger/how-to-use-the-gpu-threads-window.md) Esaminare e utilizzare i thread in esecuzione sulla GPU durante il debug.

## <a name="related-sections"></a>Sezioni correlate

[Uso di punti di interruzione](../debugger/using-breakpoints.md)
- Usare filtri dei punti di interruzione per inserire un punto di interruzione in corrispondenza di un singolo thread.

- I punti di traccia consentono di tracciare l'esecuzione dei programmi senza interruzioni. Ciò può risultare utile nello studio di problemi quali i deadlock.

  [Threading](https://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) Concetti relativi al threading nella [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] programmazione, incluso il codice di esempio.

  [Multithreading nei componenti](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) Come utilizzare il multithreading nei [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] componenti di.

  [Supporto del multithreading per il codice precedente (Visual C++)](https://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) Concetti relativi al threading e codice di esempio per i programmatori C++ che utilizzano MFC.

## <a name="see-also"></a>Vedere anche
 [Debug di thread ed elabora](../debugger/debug-threads-and-processes.md) il [debug remoto](../debugger/remote-debugging.md)
