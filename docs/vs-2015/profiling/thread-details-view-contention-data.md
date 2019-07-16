---
title: 'Visualizzazione Dettagli thread: dati sui conflitti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 16ee86e69cb3a150a98de5077aa0c545545833e8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145586"
---
# <a name="thread-details-view---contention-data"></a>Visualizzazione Dettagli thread: dati sui conflitti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La visualizzazione Dettagli thread presenta un grafico della sequenza temporale degli eventi di blocco nel thread selezionato di un'esecuzione della profilatura causati da conflitti relativi alle risorse. Si verifica un evento di blocco quando il thread viene indotto a sospendere l'esecuzione perché un altro thread ha bloccato l'accesso a una risorsa.  
  
 In questa visualizzazione la sequenza temporale dell'esecuzione del thread è rappresentata come una barra orizzontale, mentre gli eventi di blocco sono rappresentati come una barra verticale su una sequenza temporale orizzontale per il thread. Se necessario, è possibile fare zoom avanti su una sezione della sequenza temporale per visualizzare i singoli eventi. Per visualizzare il percorso di esecuzione delle funzioni che hanno condotto all'evento, fare clic sulla barra dell'evento. Le funzioni verranno visualizzate nella finestra Stack di chiamate. Quando è disponibile il codice sorgente per una funzione, è possibile fare clic sul nome della funzione per modificare il file di origine nell'IDE di Visual Studio.  
  
## <a name="navigating-the-timeline"></a>Esplorazione della sequenza temporale  
  
#### <a name="to-zoom-in-on-a-timeline-segment"></a>Per fare zoom avanti su un segmento della sequenza temporale  
  
- Fare clic e trascinare il puntatore del mouse per selezionare un'area della sequenza temporale.  
  
     Quando si rilascia il pulsante del mouse, il segmento temporale selezionato viene ingrandito. È possibile ripetere il processo per ingrandire ulteriormente il segmento. La casella di scorrimento sulla barra di scorrimento temporale rappresenta la dimensione relativa del segmento di tempo riportato nella visualizzazione.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>Per eseguire lo zoom avanti o indietro in una sequenza temporale  
  
- Fare clic su **Zoom indietro** per tornare al livello di zoom precedente.  
  
- Fare clic su **Reimposta Zoom** per mostrare l'intera sequenza temporale nella visualizzazione.  
  
#### <a name="to-view-the-call-stack-of-an-event"></a>Per visualizzare lo stack di chiamate di un evento  
  
- Nel grafico della sequenza temporale fare clic sulla barra verticale che rappresenta l'evento.  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Per visualizzare o modificare il codice sorgente di una funzione nello stack di chiamate  
  
- Nella finestra Stack di chiamate fare clic sul nome della funzione.  
  
  Il codice sorgente della funzione deve far parte del progetto corrente.  
  
#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>Per visualizzare gli eventi di conflitto di una risorsa in tutti i thread nell'esecuzione della profilatura  
  
- Nel grafico della sequenza temporale fare clic sul nome o sull'ID della risorsa.  
  
     Viene visualizzata la [visualizzazione Dettagli risorsa](../profiling/resource-details-view-contention-data.md) per la risorsa selezionata.  
  
#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>Per visualizzare i dati sui conflitti dei thread nella finestra Processi  
  
- Nel grafico della sequenza temporale fare clic su **Totale**.  
  
     Viene visualizzata la [visualizzazione Processo](../profiling/process-view-contention-data.md) con il thread selezionato.
