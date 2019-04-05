---
title: 'Procedura: Utilizzare la finestra Espressioni di controllo parallelo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: baa5381013e955dcf4b8e301bba52a28e39bfc18
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966935"
---
# <a name="how-to-use-the-parallel-watch-window"></a>Procedura: Utilizzare la finestra Espressioni di controllo parallela
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella finestra Espressione di controllo in parallelo è possibile visualizzare contemporaneamente i valori di un'espressione utilizzata in più thread. Ogni riga rappresenta un thread in esecuzione in un'applicazione, ma un thread può essere rappresentato su più righe. In particolare, ogni riga rappresenta una chiamata di funzione la cui firma della funzione corrisponde alla funzione nello stack frame corrente. È possibile ordinare, riordinare, rimuovere e raggruppare gli elementi presenti nelle colonne. È possibile aggiungere flag, rimuovere flag, bloccare (sospendere) e sbloccare (riprendere) i thread. Le colonne seguenti vengono visualizzate nella finestra **Espressione di controllo in parallelo**:  
  
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
  
3.  Sulla barra dei menu scegliere **Debug**, **Finestre**, **Espressione di controllo in parallelo** e scegliere una finestra Espressione di controllo. È possibile aprire un massimo di quattro finestre.  
  
### <a name="to-add-a-watch-expression"></a>Per aggiungere un'espressione di controllo  
  
-   Selezionare  **\<Aggiungi espressione di controllo >** e quindi specificare un'espressione di controllo.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Per aggiungere o rimuovere flag che contrassegnano un thread  
  
-   Selezionare la colonna del contrassegno per la riga o aprire il menu di scelta rapida per il thread e scegliere **Flag** oppure **Rimuovi flag**.  
  
### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag  
  
-   Scegliere il pulsante Mostra solo con flag nell'angolo superiore sinistro della **espressioni di controllo parallela** finestra.  
  
### <a name="to-switch-frames"></a>Per passare da un frame a un altro  
  
-   Fare doppio clic sulla colonna frame. (Tastiera: Selezionare la riga e premere INVIO).  
  
### <a name="to-sort-a-column"></a>Per ordinare una colonna  
  
-   Selezionare l'intestazione della colonna.  
  
### <a name="to-group-threads"></a>Per raggruppare i thread  
  
-   Aprire il menu di scelta rapida per la finestra Espressione di controllo in parallelo, scegliere **Raggruppa**, quindi scegliere la voce del sottomenu appropriata.  
  
### <a name="to-freeze-or-thaw-threads"></a>Per bloccare o sbloccare i thread  
  
-   Aprire il menu di scelta rapida per la riga e scegliere **Blocca** o **Sblocca**.  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Per esportare i dati nella finestra Espressione di controllo in parallelo  
  
-   Scegliere il pulsante **Apri in Excel** e scegliere **Apri in Excel** o **Esporta in CSV**.  
  
### <a name="to-filter-by-a-boolean-expression"></a>Per filtrare in base a un'espressione booleana  
  
-   Immettere un'espressione booleana nella casella **Filtra per espressione booleana**. Il debugger valuta l'espressione per ogni contesto del thread. Vengono visualizzate solo le righe in cui valore è `true`.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura: Usare la finestra Thread GPU](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Procedura dettagliata: Debug di un'applicazione C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
