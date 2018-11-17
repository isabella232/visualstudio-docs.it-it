---
title: 'Procedura: eseguire il Debug in un Cluster a prestazioni elevate | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-perfomance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75f2a96df18137f04b8b7637940c70378842e23d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747727"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Procedura: eseguire il debug su un cluster ad alte prestazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debug di un programma con multiprocessing in un cluster ad alte prestazioni è simile al debug di un programma normale in un computer remoto. È tuttavia necessario fare alcune considerazioni specifiche. Per requisiti generali di installazione remota, vedere [debug remoto](../debugger/remote-debugging.md).  
  
 Quando si esegue il debug in un cluster ad alte prestazioni, è possibile usare tutte le tecniche e le finestre di debug di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] disponibili per il debug remoto. Poiché, tuttavia, il debug viene eseguito in remoto, la finestra della console esterna non è disponibile.  
  
 Il **thread** finestra e **processi** sono particolarmente utili per il debug di applicazioni parallele. Per suggerimenti su come usare queste finestre, vedere [procedura: utilizzare la finestra processi](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) e [procedura: utilizzare la finestra thread](../debugger/how-to-use-the-threads-window.md).  
  
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
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debug remoto](../debugger/remote-debugging.md)   
 [Procedura: utilizzare la finestra processi](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Procedura: utilizzare la finestra thread](../debugger/how-to-use-the-threads-window.md)   
 [Thread e processi](http://msdn.microsoft.com/en-us/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Uso di punti di interruzione](../debugger/using-breakpoints.md)



