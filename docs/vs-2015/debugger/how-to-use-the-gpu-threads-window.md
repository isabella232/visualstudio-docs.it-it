---
title: 'Procedura: usare la finestra thread GPU | Microsoft Docs'
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
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8afd9cd09cf5977f58ee3a48b891f5291869b49c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799171"
---
# <a name="how-to-use-the-gpu-threads-window"></a>Procedura: utilizzare la finestra Thread GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella finestra Thread GPU è possibile esaminare e utilizzare i thread in esecuzione nella GPU nell'applicazione sottoposta a debug. Per altre informazioni sulle applicazioni eseguite nella GPU, vedere [Panoramica di C++ AMP](http://msdn.microsoft.com/library/9e593b06-6e3c-43e9-8bae-6d89efdd39fc).  
  
 La finestra Thread GPU contiene una tabella in cui ogni riga rappresenta un set di thread GPU che hanno gli stessi valori in tutte le colonne. È possibile ordinare, riordinare, rimuovere e raggruppare gli elementi presenti nelle colonne. È possibile contrassegnare, rimuovere i flag, bloccare (sospendere) e sbloccare (riprendere) i thread dalla finestra Thread GPU. Le colonne seguenti sono visualizzate nella finestra Thread GPU:  
  
- Colonna flag, nella quale è possibile contrassegnare un thread al quale si desidera prestare particolare attenzione.  
  
- Colonna del thread attivo, nella quale una freccia gialla indica un thread attivo. Una freccia indica un thread nel quale l'esecuzione si è interrotta nel debugger.  
  
- Il **conteggio dei Thread** colonna, che visualizza il numero di thread nella stessa posizione.  
  
- Il **riga** colonna, che consente di visualizzare la riga di codice in cui si trova ciascun gruppo di thread.  
  
- Il **indirizzo** colonna, che consente di visualizzare l'indirizzo dell'istruzione in cui si trova ciascun gruppo di thread. Per impostazione predefinita, questa colonna è nascosta.  
  
- Il **posizione** colonna, ovvero la posizione nel codice sorgente.  
  
- Il **stato** colonna che indica se il thread è attivo, bloccato, non è stata avviata o completata.  
  
- Il **riquadro** colonna che mostra l'indice della sezione per i thread nella riga.  
  
  Nell'intestazione della tabella sono indicati il riquadro e il thread visualizzati.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>Per visualizzare la finestra Thread GPU  
  
1.  In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto e scegliere **Proprietà**.  
  
2.  Nel **pagine delle proprietà** finestra per il progetto, sotto **delle proprietà di configurazione**, scegliere **debug**.  
  
3.  Nel **Debugger da avviare** elenco, selezionare **Debugger Windows locale**. Nel **tipo di Debugger** elenco, selezionare **solo GPU**. È necessario scegliere questo debugger per l'interruzione in corrispondenza dei punti di interruzione nel codice in esecuzione sulla GPU.  
  
4.  Fare clic sul pulsante **OK** .  
  
5.  Impostare un punto di interruzione nel codice della GPU.  
  
6.  Nella barra dei menu scegliere **Debug**, **Avvia debug**. Attendere che l'applicazione raggiunga il punto di interruzione.  
  
7.  Una barra dei menu scegliere **Debug**, **Windows**, **thread GPU**.  
  
### <a name="to-change-to-a-different-active-thread"></a>Per passare a un altro thread attivo  
  
-   Fare doppio clic sulla colonna. Sulla tastiera selezionare la riga e premere INVIO.  
  
### <a name="to-display-a-particular-tile-and-thread"></a>Per visualizzare un riquadro e un thread specifici  
  
1.  Scegliere il **Espandi selezione Thread** pulsante nella finestra thread GPU.  
  
2.  Immettere i valori del riquadro e del thread nelle caselle di testo.  
  
3.  Scegliere il pulsante con la freccia.  
  
### <a name="to-display-or-hide-a-column"></a>Per visualizzare o nascondere una colonna  
  
-   Aprire il menu di scelta rapida per la finestra thread GPU, scegliere **colonne**e quindi scegliere la colonna che si desidera visualizzare o nascondere.  
  
### <a name="to-sort-by-a-column"></a>Per ordinare per colonna  
  
-   Selezionare l'intestazione della colonna.  
  
### <a name="to-group-threads"></a>Per raggruppare i thread  
  
-   Aprire il menu di scelta rapida per la finestra thread GPU, scegliere **Group By**, quindi scegliere uno dei nomi di colonna visualizzati. Scegli **None** per separare i thread.  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>Per bloccare o sbloccare una riga di thread  
  
-   Aprire il menu di scelta rapida per la riga e scegliere **Freeze** oppure **Sblocca**.  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>Per contrassegnare o rimuovere il flag da una riga di thread  
  
-   Selezionare la colonna flag del thread o aprire il menu di scelta rapida per il thread e scegliere **Flag** oppure **Rimuovi flag**.  
  
### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag  
  
-   Scegliere il pulsante del flag nella finestra Thread GPU.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura: utilizzare la finestra Espressioni di controllo parallela](../debugger/how-to-use-the-parallel-watch-window.md)   
 [Procedura dettagliata: debug di un'applicazione C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)



