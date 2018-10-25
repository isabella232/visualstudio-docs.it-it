---
title: Impostare un'espressione di controllo per le variabili di thread in parallelo | Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9381479fdfa3d64f3504e947f49411b99d53e2d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857952"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio"></a>Impostare un'espressione di controllo per le variabili di thread in parallelo in Visual Studio
Nella finestra Espressione di controllo in parallelo è possibile visualizzare contemporaneamente i valori di un'espressione utilizzata in più thread. Ogni riga rappresenta un thread in esecuzione in un'applicazione, ma un thread può essere rappresentato su più righe. In particolare, ogni riga rappresenta una chiamata di funzione la cui firma della funzione corrisponde alla funzione nello stack frame corrente. È possibile ordinare, riordinare, rimuovere e raggruppare gli elementi presenti nelle colonne. È possibile aggiungere flag, rimuovere flag, bloccare (sospendere) e sbloccare (riprendere) i thread. Le colonne seguenti vengono visualizzate nei **espressioni di controllo parallela** finestra:  
  
- Colonna flag, nella quale è possibile contrassegnare un thread al quale si desidera prestare particolare attenzione.  
  
- La colonna del thread corrente, in cui una freccia gialla indica che il thread corrente (una freccia verde ricurva indica che un thread non correnti è il contesto di debug corrente).  
  
- Colonna configurabile che consente di visualizzare il computer, il processo, la sezione, l'attività e il thread.  
  
  > [!TIP]
  >  Per informazioni sull'attività visualizzato nei **espressioni di controllo parallela** finestra, è innanzitutto necessario aprire le **attività** finestra.  
  
- Lo spazio vuoto *Aggiungi espressione di controllo* colonne, in cui è possibile immettere espressioni di controllo.  
  
  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Per visualizzare la finestra Espressione di controllo in parallelo  
  
1.  Impostare un punto di interruzione nel codice.  
  
2.  Nella barra dei menu scegliere **Debug**, **Avvia debug**. Attendere che l'applicazione raggiunga il punto di interruzione.  
  
3.  Nella barra dei menu, scegliere **Debug**, **Windows**, **espressioni di controllo parallela**, quindi scegliere una finestra Espressioni di controllo. È possibile aprire un massimo di quattro finestre.  
  
### <a name="to-add-a-watch-expression"></a>Per aggiungere un'espressione di controllo  
  
-   Selezionare una dello spazio vuoto *Aggiungi espressione di controllo* colonne e quindi immettere un'espressione di controllo.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Per aggiungere o rimuovere flag che contrassegnano un thread  
  
-   Selezionare la colonna del contrassegno per la riga (prima colonna), oppure aprire il menu di scelta rapida per il thread e scegliere **Flag** oppure **Rimuovi flag**.  
  
### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag  
  
-   Scegliere il **Mostra solo con contrassegno** pulsante nell'angolo superiore sinistro della **espressioni di controllo parallela** finestra.  
  
### <a name="to-switch-to-another-thread"></a>Per passare a un altro thread  
  
-   Fare doppio clic sulla colonna thread corrente (seconda colonna). (tastiera: selezionare la riga e premere INVIO).  
  
### <a name="to-sort-a-column"></a>Per ordinare una colonna  
  
-   Selezionare l'intestazione della colonna.  
  
### <a name="to-group-threads"></a>Per raggruppare i thread  
  
-   Aprire il menu di scelta rapida per la finestra Espressioni di controllo parallela, scegliere **Group By**, quindi scegliere la voce del sottomenu appropriata.  
  
### <a name="to-freeze-or-thaw-threads"></a>Per bloccare o sbloccare i thread  
  
-   Aprire il menu di scelta rapida per la riga e scegliere **Freeze** oppure **Sblocca**.  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Per esportare i dati nella finestra Espressione di controllo in parallelo  
  
-   Scegliere il **Apri in Excel** , quindi scegliere **Apri in Excel** oppure **Esporta in CSV**.  
  
### <a name="to-filter-by-a-boolean-expression"></a>Per filtrare in base a un'espressione booleana  
  
-   Immettere un'espressione booleana nella **Filtra per espressione booleana** casella. Il debugger valuta l'espressione per ogni contesto del thread. Vengono visualizzate solo le righe in cui valore è `true`.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura: usare la finestra thread GPU](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Procedura dettagliata: debug di un'applicazione C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)