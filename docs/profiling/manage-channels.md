---
title: Gestire i canali | Microsoft Docs
description: Informazioni su come organizzare i canali per il processo in modo da poter esaminare modelli specifici nella visualizzazione Thread nel visualizzatore di concorrenza.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 225d261cad0e4e8c206c00e124478a83e2710845
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131287"
---
# <a name="manage-channels"></a>Gestione dei canali
Nella **visualizzazione Thread** del visualizzatore di concorrenza è possibile organizzare i canali per il processo in modo da poter esaminare modelli specifici. È possibile ordinare i canali, spostarli verso l'alto o verso il basso e nasconderli o visualizzarli.

## <a name="sort-by"></a>Sort By (Ordina per)
 Il controllo Ordina per può essere usato per ordinare i thread in base a diversi criteri, sulla base del livello di zoom corrente. Ciò è particolarmente utile quando si sta cercando un determinato modello. È possibile ordinare i thread secondo i criteri seguenti:

|Criteri|Definizione|
|--------------|----------------|
|Ora di Inizio|Ordina i thread in base all'ora di inizio. Si tratta dell'ordinamento predefinito.|
|Ora fine|Ordina i thread in base all'ora di fine.|
|Esecuzione|Ordina i thread in base alla percentuale di tempo trascorso in fase di esecuzione.|
|Sincronizzazione|Ordina i thread in base alla percentuale di tempo trascorso in fase di sincronizzazione.|
|I/O|Ordina i thread in base alla percentuale di tempo trascorso in fase di I/O (lettura e scrittura di dati).|
|Sospendi|Ordina i thread in base alla percentuale di tempo trascorso in fase di sospensione.|
|Paging|Ordina i thread in base alla percentuale di tempo trascorso in fase di paging.|
|Precedenza|Ordina i thread in base alla percentuale di tempo trascorso in fase di precedenza.|
|Elaborazione interfaccia utente|Ordina i thread in base alla percentuale di tempo trascorso in fase di elaborazione dell'interfaccia utente.|

## <a name="move-selected-channel-up-or-down"></a>Spostare il canale selezionato verso l'alto o verso il basso
 È possibile usare questi controlli per spostare un canale verso l'alto o verso il basso nell'elenco. Ad esempio, è possibile posizionare i canali correlati uno accanto all'altro in modo da poter esaminare un determinato modello o una relazione cross-thread.

## <a name="move-selected-channel-to-top-or-bottom"></a>Spostare il canale selezionato al primo o all'ultimo posto
 È possibile spostare i canali selezionati al primo o all'ultimo posto dell'elenco in modo da poter esaminare un determinato modello o escludere alcuni canali quando si esaminano gli altri.

## <a name="hide-selected-channels"></a>Nascondere i canali selezionati
 Scegliere questo controllo quando si vogliono nascondere i canali. Ad esempio, se un thread è al 100% della sincronizzazione per la durata del processo gestito, è possibile nasconderlo mentre si analizzano altri thread.

> [!NOTE]
> Se un thread viene nascosto, verrà rimosso anche dal tempo di calcolo visualizzato nella legenda attiva e nei rapporti del profilo.

## <a name="show-all-channels"></a>Visualizzare tutti i canali
 Questo controllo è attivo quando uno o più canali vengono nascosti. Se si specifica questo controllo, tutti gli elementi nascosti vengono visualizzati e vengono inclusi nel calcolo del tempo.

## <a name="move-markers-to-top"></a>Spostare i marcatori all'inizio
 Se una traccia contiene eventi marcatori, è possibile usare questo comando per spostare i canali dei marcatori all'inizio della sequenza temporale. Viene comunque mantenuto il loro ordine relativo.

## <a name="group-markers-by-thread"></a>Raggruppare i marcatori in base ai thread
 Se una traccia contiene eventi marcatori, è possibile usare questo comando per raggruppare i canali dei marcatori sotto il thread che ha generato gli eventi marcatori.  I canali dei dischi vengono spostati all'inizio dell'elenco dei canali e i canali GPU vengono spostati alla fine.

## <a name="see-also"></a>Vedi anche
- [Controllo Zoom (visualizzazione Thread)](../profiling/zoom-control-threads-view.md)
- [Modalità misura attivata/disattivata](../profiling/measure-mode-on-off.md)
- [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)