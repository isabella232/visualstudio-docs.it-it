---
title: Eseguire il debug in High-Performance cluster | Microsoft Docs
description: Informazioni sulle caratteristiche particolari del debug di un programma multiprocessing in un cluster ad alte prestazioni. Due finestre sono particolarmente utili e sono disponibili tecniche speciali.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c4e6bffa006fac3408bc3b5459cdeee92c9a636f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710394"
---
# <a name="how-to-debug-on-a-high-performance-cluster-c-visual-basic-c"></a>Procedura: Eseguire il debug in un cluster High-Performance (C#, Visual Basic, C++)

Il debug di un programma con multiprocessing in un cluster ad alte prestazioni è simile al debug di un programma normale in un computer remoto. È tuttavia necessario fare alcune considerazioni specifiche. Per i requisiti generali per l'installazione remota, vedere [Debug remoto](../debugger/remote-debugging.md).

 Quando si esegue il debug in un cluster ad alte prestazioni, è possibile usare tutte le tecniche e le finestre di debug di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] disponibili per il debug remoto. Poiché, tuttavia, il debug viene eseguito in remoto, la finestra della console esterna non è disponibile.

 Le finestre **Thread** e **Processi** sono particolarmente utili per il debug di applicazioni parallele. Per suggerimenti su come usare queste finestre, vedere [come: Utilizzare la finestra processi](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100)) e [procedura dettagliata: Eseguire il debug con la finestra Thread](../debugger/how-to-use-the-threads-window.md).

 Nelle procedure riportate di seguito sono illustrate alcune tecniche che risultano particolarmente utili per il debug in un cluster ad alte prestazioni.

 Quando si esegue il debug di un'applicazione parallela, è possibile impostare un punto di interruzione in un thread, in un processo o in un computer specifico. A tale scopo, è possibile creare un punto di interruzione normale e quindi aggiungere un apposito filtro.

### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Per aprire la finestra di dialogo Filtro punto di interruzione

1. Fare clic con il pulsante destro del mouse su un glifo del punto di interruzione in una finestra di origine, nella finestra **Disassembly**, nella finestra **Stack di chiamate** o nella finestra **Punti di interruzione**.

2. Scegliere **Filtro** dal menu di scelta rapida. Questa opzione può essere presente nel menu di livello superiore o nel sottomenu sotto **Punti di interruzione**.

### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Per impostare un punto di interruzione in un computer specifico

1. Ottenere il nome del computer nella finestra **Processi**.

2. Selezionare un punto di interruzione e aprire la finestra di dialogo **Filtro punto di interruzione** come descritto nella procedura precedente.

3. Nella finestra di dialogo **Filtro punto di interruzione** digitare:

     MachineName =*yourmachinename*

     Per creare un filtro più complesso, è possibile combinare clausole utilizzando `&`, l'operatore AND, `||`, l'operatore OR, `!`, l'operatore NOT e le parentesi.

4. Fare clic su **OK**.

### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Per impostare un punto di interruzione in un processo specifico

1. Ottenere il nome o il numero di ID del processo nella finestra **Processi**.

2. Selezionare un punto di interruzione e aprire la finestra di dialogo **Filtro punto di interruzione** come descritto nella prima procedura.

3. Nella finestra di dialogo **Filtro punto di interruzione** digitare:

     `ProcessName =`  *yourprocessname*

     -oppure-

     `ProcessID =` *yourprocessIDnumber*

     Per creare un filtro più complesso, è possibile combinare clausole utilizzando `&`, l'operatore AND, `||`, l'operatore OR, `!`, l'operatore NOT e le parentesi.

4. Fare clic su **OK**.

### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Per impostare un punto di interruzione in un thread specifico

1. Ottenere il nome o il numero ID del thread nella finestra **Thread**.

2. Selezionare un punto di interruzione e aprire la finestra di dialogo **Filtro punto di interruzione** come descritto nella prima procedura.

3. Nella finestra di dialogo **Filtro punto di interruzione** digitare:

     `ThreadName =` *yourthreadname*

     -oppure-

     `ThreadID =` *yourthreadIDnumber*

     Per creare un filtro più complesso, è possibile combinare clausole utilizzando `&`, l'operatore AND, `||`, l'operatore OR, `!`, l'operatore NOT e le parentesi.

4. Fare clic su **OK**.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato come creare un filtro per un punto di interruzione in un computer denominato `marvin` e un thread denominato `fourier1`.

`(MachineName = marvin) & (ThreadName = fourier1)`

## <a name="see-also"></a>Vedi anche
- [Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Debug remoto](../debugger/remote-debugging.md)
- [Procedura: Usare la finestra Processi](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))
- [Informazioni di base Debug di app multithreading](../debugger/get-started-debugging-multithreaded-apps.md)
- [Thread e processi](/previous-versions/visualstudio/visual-studio-2010/ms164740(v=vs.100))
- [Uso di punti di interruzione](../debugger/using-breakpoints.md)