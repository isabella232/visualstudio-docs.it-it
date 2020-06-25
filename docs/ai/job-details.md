---
title: Visualizzazione dei processi recenti
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 2e404d6a258ebb480b3eb02e615097872714db03
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371547"
---
# <a name="view-recent-job-performance-and-details"></a>Visualizzare le prestazioni e i dettagli di processi recenti

Dopo l'invio dei processi è possibile visualizzare l'elenco dei processi per controllare il relativo stato, la durata e altri dettagli.

1. Nel **Esplora server**espandere il contesto di calcolo specifico.
2. Fare doppio clic su **Processi**.
3. Verrà visualizzato l'elenco dei processi inviati a tale contesto di calcolo.
4. Selezionare un **processo** specifico nell'elenco per visualizzare i dettagli.

![Monitorare i processi](media/job-details/monitor-jobs.png)

> La cronologia dei processi inviati alle macchine virtuali di Linux viene archiviata nella directory /tmp nella macchina virtuale. La cronologia viene pertanto cancellata a ogni riavvio. Per ottenere un record permanente della cronologia dei processi, configurare la macchina virtuale come contesto di calcolo in Azure Machine Learning, quindi inviare il processo ad Azure Machine Learning selezionando la macchina virtuale come contesto di calcolo.
