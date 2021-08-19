---
title: Visualizzazione Utilizzo | Microsoft Docs
description: Nella visualizzazione Utilizzo vengono visualizzate informazioni su CPU, GPU e altre risorse di sistema usate dal processo corrente.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cpuutilization
helpviewer_keywords:
- Concurrency Visualizer, CPU Utilization View
ms.assetid: b4f7ceab-3653-4069-bb74-c309aec62866
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0f169bebc65f6d0418717e6087a7b19c6f615505
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140830"
---
# <a name="utilization-view"></a>Visualizzazione Utilizzo
La **visualizzazione Utilizzo** contiene informazioni relative a CPU, GPU e altre risorse di sistema usate dal processo corrente (scegliere **Analizza** > **Visualizzatore di concorrenza** per avviare il visualizzatore di concorrenza). Viene indicato l'utilizzo medio dei core da parte del processo analizzato, del processo inattivo, del processo di sistema e di altri processi in esecuzione nel sistema nel tempo. Non viene indicato quale core specifico è attivo in un momento determinato. Ad esempio, se due core sono in esecuzione al 50% per un determinato periodo di tempo, il grafico indica che viene usato un solo core logico. La visualizzazione viene generata dividendo il tempo di profilatura in brevi segmenti di tempo. Per ogni segmento, nel grafico viene rappresentato il numero medio di thread di processo in esecuzione nei core logici durante l'intervallo.

 ![Visualizzazione Utilizzo CPU](../profiling/media/vsts_ppacpuutil.png "VSTS_PPAcpuUtil")

 Il grafico mostra il tempo (sull'asse x) e la media dei core logici usati dal processo di destinazione, dal processo inattivo e dal processo di sistema. Il processo inattivo mostra i core inattivi. Il processo di sistema è un processo Windows che può eseguire operazioni per conto di altri processi. I processi rimanenti in esecuzione nell'account di sistema per l'utilizzo di eventuali core rimanenti.

 Sull'asse y viene indicato il numero di core logici. Windows considera il supporto multithread simultaneo nell'hardware come core logici (ad esempio, Hyper-Threading). Di conseguenza, un sistema dotato di un processore quad core che supporta due thread hardware per ogni core viene visualizzato come un sistema con otto core logici. Questo vale anche per la visualizzazione Core. Per altre informazioni, vedere [Visualizzazione Core.](../profiling/cores-view.md)

 Il grafico Attività GPU mostra il numero di motori di DirectX in uso nel tempo.  Un motore è in uso se sta elaborando un pacchetto DMA.  Il grafico non mostra lo specifico motore di DirectX (ad esempio, motore 3D, motore video e altri).

## <a name="purpose"></a>Scopo
 È consigliabile usare la visualizzazione Utilizzo come punto di partenza per le analisi delle prestazioni quando si usa il visualizzatore di concorrenza. Poiché fornisce una panoramica del livello di concorrenza in un'app nel tempo, è possibile usare questa visualizzazione per identificare rapidamente le aree che richiedono l'ottimizzazione o la parallelizzazione delle prestazioni.

 Se è interessati all'ottimizzazione delle prestazioni, può essere utile tentare di identificare i comportamenti che non soddisfano le aspettative. È possibile verificare se sono presenti aree con un utilizzo ridotto dei core logici della CPU e identificare la causa del problema. È anche possibile tentare di individuare schemi di utilizzo tra la CPU e la GPU.

 Se si è interessati alla parallelizzazione di un'app, è possibile cercare le aree di esecuzione associate alla CPU o quelle in cui la CPU non viene usata.

 Le aree associate alla CPU sono di colore verde. Se l'applicazione è seriale, il grafico mostra l'utilizzo di un solo core.

 Le aree in cui la CPU non viene usata sono visualizzate in grigio. Queste aree potrebbero rappresentare punti in cui l'app è inattiva o esegue attività di I/O di blocco che offrono opportunità di parallelismo attraverso la sovrapposizione con altre operazioni associate alla CPU.

 Quando si individua un comportamento di proprio interesse, è possibile ingrandire l'area selezionandola. Dopo avere eseguito lo zoom, è possibile passare alla visualizzazione Thread o alla visualizzazione Core per un'analisi più dettagliata.

 Se si usa la GPU con C++ AMP o DirectX, potrebbe essere utile identificare il numero di motori GPU in uso o le aree di inattività imprevista della GPU.

## <a name="zoom"></a>Zoom
 Per ingrandire il grafico Utilizzo CPU o il grafico Attività GPU, selezionare una sezione o usare il dispositivo di scorrimento dello zoom sopra il grafico. L'impostazione dello zoom viene mantenuta quando si passa ad altre visualizzazioni. Per eseguire lo zoom indietro, usare il dispositivo di scorrimento dello zoom. È anche possibile eseguire lo zoom usando + **CTRL+FRECCIA SU.**

## <a name="see-also"></a>Vedi anche
- [Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)
- [Visualizzazione Core](../profiling/cores-view.md)