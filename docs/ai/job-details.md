---
title: Visualizzazione dei processi recenti
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 79b396946666077dcdedb3ee2a5ab891c2bb4fb8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "72777400"
---
# <a name="view-recent-job-performance-and-details"></a>Visualizzare le prestazioni e i dettagli di processi recenti

Dopo l'invio dei processi è possibile visualizzare l'elenco dei processi per controllare il relativo stato, la durata e altri dettagli.

1. In **Esplora server**espandere il contesto di calcolo specifico.
2. Fare doppio clic su **Processi**.
3. Verrà visualizzato l'elenco dei processi inviati a tale contesto di calcolo.
4. Selezionare un **lavoro** specifico nell'elenco per visualizzare i dettagli.

![Monitorare i processi](media/job-details/monitor-jobs.png)

> La cronologia dei processi inviati alle macchine virtuali di Linux viene archiviata nella directory /tmp nella macchina virtuale. La cronologia viene pertanto cancellata a ogni riavvio. Per ottenere un record permanente della cronologia dei processi, configurare la macchina virtuale come contesto di calcolo in Azure Machine Learning, quindi inviare il processo ad Azure Machine Learning selezionando la macchina virtuale come contesto di calcolo.
