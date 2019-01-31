---
title: Visualizzazione thread GPU nel Debugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4c246aec092cbaea8d5caf22cb8f204d32533ddb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952821"
---
# <a name="how-to-use-the-gpu-threads-window-c"></a>Procedura: Utilizzare la finestra thread GPU (C++)
Nella finestra Thread GPU è possibile esaminare e utilizzare i thread in esecuzione nella GPU nell'applicazione sottoposta a debug. Per altre informazioni sulle applicazioni eseguite nella GPU, vedere [Panoramica di C++ AMP](/cpp/parallel/amp/cpp-amp-overview).  
  
 La finestra Thread GPU contiene una tabella in cui ogni riga rappresenta un set di thread GPU che hanno gli stessi valori in tutte le colonne. È possibile ordinare, riordinare, rimuovere e raggruppare gli elementi presenti nelle colonne. È possibile contrassegnare, rimuovere i flag, bloccare (sospendere) e sbloccare (riprendere) i thread dalla finestra Thread GPU. Le colonne seguenti sono visualizzate nella finestra Thread GPU:  
  
- Colonna flag, nella quale è possibile contrassegnare un thread al quale si desidera prestare particolare attenzione.  
  
- Il thread colonna corrente, in cui una freccia gialla indica che il thread corrente.  
  
- Colonna **Conteggio thread**, che visualizza il numero di thread nella stessa posizione.  
  
- Colonna **Riga**, che visualizza la riga di codice in cui si trova ciascun gruppo di thread.  
  
- Colonna **Indirizzo**, che visualizza l'indirizzo dell'istruzione in cui si trova ciascun gruppo di thread. Per impostazione predefinita, questa colonna è nascosta.  
  
- Colonna **Posizione**, che indica la posizione nel codice sorgente.  
  
- Colonna **Stato**, che indica se il thread è attivo, bloccato, non avviato o completo.  
  
- Colonna **Sezione**, che indica l'indice della sezione per i thread nella riga.  
  
  Nell'intestazione della tabella sono indicati il riquadro e il thread visualizzati.  
  
  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>Per visualizzare la finestra Thread GPU  
  
1.  In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto e scegliere **Proprietà**.  
  
2.  Nella finestra **Pagine delle proprietà** per il progetto, in **Proprietà di configurazione** scegliere **Debug**.  
  
3.  Nell'elenco **Debugger da avviare** selezionare **Debugger Windows locale**. Nell'elenco **Tipo di debugger** selezionare **Solo GPU**. È necessario scegliere questo debugger per l'interruzione in corrispondenza dei punti di interruzione nel codice in esecuzione sulla GPU.  
  
4.  Fare clic sul pulsante **OK** .  
  
5.  Impostare un punto di interruzione nel codice della GPU.  
  
6.  Nella barra dei menu scegliere **Debug**, **Avvia debug**. Attendere che l'applicazione raggiunga il punto di interruzione.  
  
7.  Nella barra dei menu scegliere **Debug**, **Windows**, **Thread GPU**.  
  
### <a name="to-switch-to-a-different-thread"></a>Per passare a un altro thread  
  
-   Fare doppio clic sulla colonna. (Tastiera: Selezionare la riga e premere INVIO).  
  
### <a name="to-display-a-particular-tile-and-thread"></a>Per visualizzare un riquadro e un thread specifici  
  
1.  Scegliere il pulsante **Espandi selezione thread** nella finestra Thread GPU.  
  
2.  Immettere i valori del riquadro e del thread nelle caselle di testo.  
  
3.  Scegliere il pulsante con la freccia.  
  
### <a name="to-display-or-hide-a-column"></a>Per visualizzare o nascondere una colonna  
  
-   Aprire il menu di scelta rapida per la finestra Thread GPU, scegliere **Colonne**, quindi scegliere la colonna da visualizzare o nascondere.  
  
### <a name="to-sort-by-a-column"></a>Per ordinare per colonna  
  
-   Selezionare l'intestazione della colonna.  
  
### <a name="to-group-threads"></a>Per raggruppare i thread  
  
-   Aprire il menu di scelta rapida per la finestra Thread GPU, scegliere **Raggruppa**, quindi scegliere uno dei nomi di colonna visualizzati. Scegliere **Nessuno** per separare i thread.  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>Per bloccare o sbloccare una riga di thread  
  
-   Aprire il menu di scelta rapida per la riga e scegliere **Blocca** o **Sblocca**.  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>Per contrassegnare o rimuovere il flag da una riga di thread  
  
-   Selezionare la colonna dei flag per il thread o aprire il menu di scelta rapida per il thread e scegliere **Contrassegna** o **Rimuovi flag**.  
  
### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag  
  
-   Scegliere il pulsante del flag nella finestra Thread GPU.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura: Usare la finestra Espressione di controllo in parallelo](../debugger/how-to-use-the-parallel-watch-window.md)   
 [Procedura dettagliata: Debug di un'applicazione C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)