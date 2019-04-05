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
ms.openlocfilehash: 821396989a2de9444fdbf3499709588d00e66b45
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "59000876"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debug di applicazioni multithreading in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un thread è una sequenza di istruzioni in base alla quale il sistema operativo esegue l'allocazione del tempo processore. Ogni processo in esecuzione nel sistema operativo è composto da almeno un thread. I processi composti da più di un thread sono detti multithreading.

 I computer multiprocessore, i processori multicore e i processi hyperthreading sono in grado di eseguire contemporaneamente più thread. Se da un lato l'elaborazione parallela di più thread può migliorare notevolmente le prestazioni dei programmi, dall'altro può rendere il debug più difficoltoso poiché introduce la necessità di tenere traccia di più thread.

 Il multithreading introduce inoltre nuovi tipi di possibili bug. Accade spesso, ad esempio, che due o più thread debbano accedere alla stessa risorsa, alla quale però può accedere un solo thread alla volta. Deve necessariamente esistere una qualche forma di esclusione reciproca per garantire l'accesso alla risorsa di un solo thread alla volta. Se l'esclusione reciproca viene eseguita in modo non corretto, è possibile creare un *deadlock* condizione in cui è possibile eseguire alcun thread. I deadlock possono rappresentare un problema particolarmente difficile da risolvere con il debug.

 Visual Studio offre un' **thread** finestra, una finestra thread GPU, una finestra Espressioni di controllo parallelo e altre funzionalità che rendono il debug multithreading. Il modo migliore per acquisire ulteriori informazioni sulle nuove funzionalità dell'interfaccia di threading consiste nell'eseguire le procedure dettagliate. Vedere [Procedura dettagliata: Debug di un'applicazione multithreading](../debugger/walkthrough-debugging-a-multithreaded-application.md) e [procedura dettagliata: Debug di un'applicazione C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).

 Visual Studio offre anche potenti punti di interruzione e punti di analisi che possono rivelarsi molto utili per il debug di applicazioni multithreading. È possibile applicare filtri dei punti di interruzione per inserire punti di interruzione in corrispondenza di singoli thread. Vedere [usando i punti di interruzione](../debugger/using-breakpoints.md)

 Il debug di un'applicazione multithreading dotata di un'interfaccia utente può essere particolarmente complesso. In tal caso, potrebbe essere necessario eseguire l'applicazione in un secondo computer e utilizzare il debug remoto. Per informazioni, vedere [debug remoto](../debugger/remote-debugging.md).

## <a name="in-this-section"></a>In questa sezione
 [Eseguire il debug di thread e processi](../debugger/debug-threads-and-processes.md) illustra le nozioni fondamentali di debug di thread e processi.

 [Eseguire il debug di più processi](../debugger/debug-multiple-processes.md) spiega come eseguire il debug di più processi.

 [Procedura: Utilizzare la finestra thread](../debugger/how-to-use-the-threads-window.md) procedure utili per il debug dei thread con il **thread** finestra.

 [Procedura: Passare a un altro Thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md) tre modi per passare il contesto di debug a un altro thread.

 [Procedura: Rimuovi flag del thread e flag](../debugger/how-to-flag-and-unflag-threads.md) contrassegno o flag ai thread che si desidera prestare particolare attenzione durante il debug.

 [Procedura: Impostare il nome di un Thread in codice nativo](../debugger/how-to-set-a-thread-name-in-native-code.md) attribuzione di un nome da visualizzare nel **thread** finestra.

 [Procedura: Impostare il nome di un Thread in codice gestito](../debugger/how-to-set-a-thread-name-in-managed-code.md) attribuzione di un nome da visualizzare nel **thread** finestra.

 [Procedura dettagliata: Debug di un'applicazione multithreading](../debugger/walkthrough-debugging-a-multithreaded-application.md).
Presentazione guidata delle funzionalità di debug dei thread, con particolare attenzione alle funzionalità procedura [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].

 [Procedura: Eseguire il debug in un Cluster ad alte prestazioni](../debugger/how-to-debug-on-a-high-performance-cluster.md) tecniche per il debug di un'applicazione che viene eseguito in un cluster ad alte prestazioni.

 [Suggerimenti per il debug di thread in codice nativo](../debugger/tips-for-debugging-threads-in-native-code.md) semplici tecniche che possono essere utili per il debug di thread nativi.

 [Uso della finestra attività](../debugger/using-the-tasks-window.md) Mostra un elenco di tutti gli oggetti attività gestiti o nativi incluso il relativo stato e altre informazioni utili.

 [Usando la finestra Stack in parallelo](../debugger/using-the-parallel-stacks-window.md) chiamata Mostra gli stack di più thread (o attività) in un'unica visualizzazione e riunisce inoltre i segmenti dello stack comuni ai vari thread (o attività).

 [Procedura dettagliata: Debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md) procedura dettagliata che illustra come usare le finestre attività in parallelo e stack in parallelo.

 [Procedura: Utilizzare la finestra Espressioni di controllo in parallelo](../debugger/how-to-use-the-parallel-watch-window.md) ispezionare Value ed espressioni in più thread.

 [Procedura: Utilizzare la finestra thread GPU](../debugger/how-to-use-the-gpu-threads-window.md) esaminare e utilizzare i thread in esecuzione sulla GPU durante il debug.

## <a name="related-sections"></a>Sezioni correlate
 [Uso di punti di interruzione](../debugger/using-breakpoints.md)
 -   Usare filtri dei punti di interruzione per inserire un punto di interruzione in corrispondenza di un singolo thread.

- I punti di traccia consentono di tracciare l'esecuzione dei programmi senza interruzioni. Ciò può risultare utile nello studio di problemi quali i deadlock.

  [Threading](http://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) concetti di Threading [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] programmazione, inclusi esempi di codice.

  [Multithreading nei componenti](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) come usare il multithreading nel [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] componenti.

  [Supporto del multithreading per il codice precedente (Visual C++)](http://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) informazioni sul Threading ed esempio di codice per i programmatori C++ con MFC.

## <a name="see-also"></a>Vedere anche
 [Eseguire il debug di thread e processi](../debugger/debug-threads-and-processes.md) [debug remoto](../debugger/remote-debugging.md)
