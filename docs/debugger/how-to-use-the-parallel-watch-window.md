---
title: Impostare un'espressione di controllo sulle variabili nei thread paralleli | Microsoft Docs
ms.date: 04/25/2017
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fb0d5ac60ea5ab89b02a624488b5df4f8a7164b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348626"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio-c-visual-basic-c"></a>Impostare un'espressione di controllo sulle variabili nei thread paralleli in Visual Studio (C#, Visual Basic, C++)
Nella finestra Espressione di controllo in parallelo è possibile visualizzare contemporaneamente i valori di un'espressione utilizzata in più thread. Ogni riga rappresenta un thread in esecuzione in un'applicazione, ma un thread può essere rappresentato su più righe. In particolare, ogni riga rappresenta una chiamata di funzione la cui firma della funzione corrisponde alla funzione nello stack frame corrente. È possibile ordinare, riordinare, rimuovere e raggruppare gli elementi presenti nelle colonne. È possibile aggiungere flag, rimuovere flag, bloccare (sospendere) e sbloccare (riprendere) i thread. Le colonne seguenti vengono visualizzate nella finestra **Espressione di controllo in parallelo**:

- Colonna flag, nella quale è possibile contrassegnare un thread al quale si desidera prestare particolare attenzione.

- La colonna del thread corrente, in cui una freccia gialla indica il thread corrente (una freccia verde con una coda riccia indica che un thread non corrente ha il contesto del debugger corrente).

- Colonna configurabile che consente di visualizzare il computer, il processo, la sezione, l'attività e il thread.

  > [!TIP]
  > Per visualizzare le informazioni sulle attività nella finestra espressione di **controllo in parallelo** , è innanzitutto necessario aprire la finestra **attività** .

- Colonne di espressioni di *controllo di aggiunta* vuote, in cui è possibile immettere espressioni da controllare.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-parallel-watch-window"></a>Per visualizzare la finestra Espressione di controllo in parallelo

1. Impostare un punto di interruzione nel codice.

2. Nella barra dei menu scegliere **Debug**, **Avvia debug**. Attendere che l'applicazione raggiunga il punto di interruzione.

3. Sulla barra dei menu scegliere **Debug**, **Finestre**, **Espressione di controllo in parallelo** e scegliere una finestra Espressione di controllo. È possibile aprire un massimo di quattro finestre.

### <a name="to-add-a-watch-expression"></a>Per aggiungere un'espressione di controllo

- Selezionare una delle colonne Aggiungi espressione di *controllo* vuota e quindi immettere un'espressione di controllo.

### <a name="to-flag-or-unflag-a-thread"></a>Per aggiungere o rimuovere flag che contrassegnano un thread

- Selezionare la colonna flag per la riga (prima colonna) oppure aprire il menu di scelta rapida per il thread e scegliere **flag o Rimuovi** **flag**.

### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag

- Scegliere il pulsante **Mostra solo con flag** nell'angolo superiore sinistro della finestra espressione di **controllo in parallelo** .

### <a name="to-switch-to-another-thread"></a>Per passare a un altro thread

- Fare doppio clic sulla colonna thread corrente (seconda colonna). (tastiera: selezionare la riga e premere INVIO).

### <a name="to-sort-a-column"></a>Per ordinare una colonna

- Selezionare l'intestazione della colonna.

### <a name="to-group-threads"></a>Per raggruppare i thread

- Aprire il menu di scelta rapida per la finestra Espressione di controllo in parallelo, scegliere **Raggruppa**, quindi scegliere la voce del sottomenu appropriata.

### <a name="to-freeze-or-thaw-threads"></a>Per bloccare o sbloccare i thread

- Aprire il menu di scelta rapida per la riga e scegliere **Blocca** o **Sblocca**.

### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Per esportare i dati nella finestra Espressione di controllo in parallelo

- Scegliere il pulsante **Apri in Excel** e scegliere **Apri in Excel** o **Esporta in CSV**.

### <a name="to-filter-by-a-boolean-expression"></a>Per filtrare in base a un'espressione booleana

- Immettere un'espressione booleana nella casella **Filtra per espressione booleana**. Il debugger valuta l'espressione per ogni contesto del thread. Vengono visualizzate solo le righe in cui valore è `true`.

## <a name="see-also"></a>Vedere anche
- [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Procedura: usare la finestra thread GPU](../debugger/how-to-use-the-gpu-threads-window.md)
- [Procedura dettagliata: debug di un'applicazione C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)