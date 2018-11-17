---
title: 'Procedura: utilizzare la finestra Espressioni di controllo parallelo | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43783ad2b7d0f08aace55ff3b974d64301a38db2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753120"
---
# <a name="how-to-use-the-parallel-watch-window"></a>Procedura: utilizzare la finestra Espressione di controllo in parallelo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella finestra Espressione di controllo in parallelo è possibile visualizzare contemporaneamente i valori di un'espressione utilizzata in più thread. Ogni riga rappresenta un thread in esecuzione in un'applicazione, ma un thread può essere rappresentato su più righe. In particolare, ogni riga rappresenta una chiamata di funzione la cui firma della funzione corrisponde alla funzione nello stack frame corrente. È possibile ordinare, riordinare, rimuovere e raggruppare gli elementi presenti nelle colonne. È possibile aggiungere flag, rimuovere flag, bloccare (sospendere) e sbloccare (riprendere) i thread. Le colonne seguenti vengono visualizzate nei **espressioni di controllo parallela** finestra:  
  
- Colonna flag, nella quale è possibile contrassegnare un thread al quale si desidera prestare particolare attenzione.  
  
- Colonna frame, in cui una freccia indica il frame selezionato.  
  
- Colonna configurabile che consente di visualizzare il computer, il processo, la sezione, l'attività e il thread.  
  
  > [!TIP]
  >  È necessario aprire la **l'attività parallela** finestra per visualizzare le informazioni sull'attività nel **espressioni di controllo parallela** finestra.  
  
- Il  **\<Aggiungi espressione di controllo >** colonna, in cui è possibile immettere espressioni di controllo.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Per visualizzare la finestra Espressione di controllo in parallelo  
  
1.  Impostare un punto di interruzione nel codice.  
  
2.  Nella barra dei menu scegliere **Debug**, **Avvia debug**. Attendere che l'applicazione raggiunga il punto di interruzione.  
  
3.  Nella barra dei menu, scegliere **Debug**, **Windows**, **espressioni di controllo parallela**, quindi scegliere una finestra Espressioni di controllo. È possibile aprire un massimo di quattro finestre.  
  
### <a name="to-add-a-watch-expression"></a>Per aggiungere un'espressione di controllo  
  
-   Selezionare  **\<Aggiungi espressione di controllo >** e quindi specificare un'espressione di controllo.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Per aggiungere o rimuovere flag che contrassegnano un thread  
  
-   Selezionare la colonna del contrassegno per la riga o aprire il menu di scelta rapida per il thread e scegliere **Flag** oppure **Rimuovi flag**.  
  
### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag  
  
-   Scegliere il pulsante Mostra solo con flag nell'angolo superiore sinistro della **espressioni di controllo parallela** finestra.  
  
### <a name="to-switch-frames"></a>Per passare da un frame a un altro  
  
-   Fare doppio clic sulla colonna frame. (tastiera: selezionare la riga e premere INVIO).  
  
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
 [Procedura dettagliata: debug di un'applicazione C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)



