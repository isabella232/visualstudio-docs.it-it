---
title: 'Procedura: eseguire il Debug in un Cluster a prestazioni elevate | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-perfomance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9964621c216d058581d9298956ba90ac6cdbef86
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280792"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Procedura: eseguire il debug su un cluster ad alte prestazioni
Il debug di un programma con multiprocessing in un cluster ad alte prestazioni è simile al debug di un programma normale in un computer remoto. È tuttavia necessario fare alcune considerazioni specifiche. Per requisiti generali di installazione remota, vedere [debug remoto](../debugger/remote-debugging.md).  
  
 Quando si esegue il debug in un cluster ad alte prestazioni, è possibile usare tutte le tecniche e le finestre di debug di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] disponibili per il debug remoto. Poiché, tuttavia, il debug viene eseguito in remoto, la finestra della console esterna non è disponibile.  
  
 Il **thread** finestra e **processi** sono particolarmente utili per il debug di applicazioni parallele. Per suggerimenti su come usare queste finestre, vedere [procedura: utilizzare la finestra processi](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100)) e [procedura dettagliata: eseguire il Debug usando la finestra thread](../debugger/how-to-use-the-threads-window.md).  
  
 Nelle procedure riportate di seguito sono illustrate alcune tecniche che risultano particolarmente utili per il debug in un cluster ad alte prestazioni.  
  
 Quando si esegue il debug di un'applicazione parallela, è possibile impostare un punto di interruzione in un thread, in un processo o in un computer specifico. A tale scopo, è possibile creare un punto di interruzione normale e quindi aggiungere un apposito filtro.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Per aprire la finestra di dialogo Filtro punto di interruzione  
  
1.  Fare doppio clic su un glifo del punto di interruzione in una finestra di origine, il **Disassembly** finestra, il **Stack di chiamate** finestra o la **i punti di interruzione** finestra.  
  
2.  Nel menu di scelta rapida, fare clic su **filtro**. Questa opzione può essere presente nella parte superiore livello o nel sottomenu sotto **i punti di interruzione**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Per impostare un punto di interruzione in un computer specifico  
  
1.  Ottenere il nome del computer dal **processi** finestra.  
  
2.  Selezionare un punto di interruzione e aprire il **Filtro punto di interruzione** finestra di dialogo come descritto nella procedura precedente.  
  
3.  Nel **Filtro punto di interruzione** nella finestra di dialogo, digitare:  
  
     MachineName =*nomecomputer*  
  
     Per creare un filtro più complesso, è possibile combinare clausole utilizzando `&`, l'operatore AND, `||`, l'operatore OR, `!`, l'operatore NOT e le parentesi.  
  
4.  Fare clic su **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Per impostare un punto di interruzione in un processo specifico  
  
1.  Ottenere il nome del processo o il numero di ID di processo di **processi** finestra.  
  
2.  Selezionare un punto di interruzione e aprire il **Filtro punto di interruzione** finestra di dialogo come illustrato nella prima procedura.  
  
3.  Nel **Filtro punto di interruzione** nella finestra di dialogo, digitare:  
  
     `ProcessName =`  *yourprocessname*  
  
     -oppure-  
  
     `ProcessID =` *yourprocessIDnumber*  
  
     Per creare un filtro più complesso, è possibile combinare clausole utilizzando `&`, l'operatore AND, `||`, l'operatore OR, `!`, l'operatore NOT e le parentesi.  
  
4.  Fare clic su **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Per impostare un punto di interruzione in un thread specifico  
  
1.  Ottenere il nome o numero di ID di thread di **thread** finestra.  
  
2.  Selezionare un punto di interruzione e aprire il **Filtro punto di interruzione** come descritto nella prima procedura di finestra di dialogo.  
  
3.  Nel **Filtro punto di interruzione** nella finestra di dialogo, digitare:  
  
     `ThreadName =` *yourthreadname*  
  
     -oppure-  
  
     `ThreadID =` *yourthreadIDnumber*  
  
     Per creare un filtro più complesso, è possibile combinare clausole utilizzando `&`, l'operatore AND, `||`, l'operatore OR, `!`, l'operatore NOT e le parentesi.  
  
4.  Fare clic su **OK**.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come creare un filtro per un punto di interruzione in un computer denominato `marvin` e un thread denominato `fourier1`.  
  
`(MachineName = marvin) & (ThreadName = fourier1)`  

  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debug remoto](../debugger/remote-debugging.md)   
 [Procedura: utilizzare la finestra processi](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))   
 [Iniziare il debug di applicazioni multithreading](../debugger/get-started-debugging-multithreaded-apps.md)   
 [Thread e processi](/previous-versions/visualstudio/visual-studio-2010/ms164740(v=vs.100))   
 [Uso di punti di interruzione](../debugger/using-breakpoints.md)