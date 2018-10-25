---
ms.technology: vs-ai-tools
ms.openlocfilehash: ebf412dbeb4e0ecc391c52d7da5ea49d12e6231f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930362"
---
# <a name="view-recent-job-performance-and-details"></a>Visualizzare le prestazioni e i dettagli di processi recenti

Dopo l'invio dei processi è possibile visualizzare l'elenco dei processi per controllare il relativo stato, la durata e altri dettagli.

1. In **Esplora server** espandere il contesto di calcolo specifico.
2. Fare doppio clic su **Processi**.
3. Verrà visualizzato l'elenco dei processi inviati a tale contesto di calcolo.
4. Selezionare un **processo** specifico dall'elenco per visualizzare i dettagli.

![Monitorare i processi](media/job-details/monitor-jobs.png)

> La cronologia dei processi inviati alle macchine virtuali di Linux viene archiviata nella directory /tmp nella macchina virtuale. La cronologia viene pertanto cancellata a ogni riavvio. Per ottenere un record permanente della cronologia dei processi, configurare la macchina virtuale come contesto di calcolo in Azure Machine Learning, quindi inviare il processo ad Azure Machine Learning selezionando la macchina virtuale come contesto di calcolo.