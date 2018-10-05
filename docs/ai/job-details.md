---
ms.technology: vs-ai-tools
ms.openlocfilehash: b7c8de18ba0083d31287fe862ab0015cb210bce1
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279635"
---
# <a name="view-recent-job-performance-and-details"></a>Visualizzare le prestazioni e i dettagli di processi recenti
Dopo l'invio dei processi è possibile visualizzare l'elenco dei processi per controllare il relativo stato, la durata e altri dettagli.

1. In **Esplora server** espandere il contesto di calcolo specifico.
1. Fare doppio clic su **Processi**.
1. Verrà visualizzato l'elenco dei processi inviati a tale contesto di calcolo.
1. Selezionare un **processo** specifico dall'elenco per visualizzare i dettagli.

![Monitorare i processi](media\job-details\monitor-jobs.png)

> La cronologia dei processi inviati alle macchine virtuali di Linux viene archiviata nella directory /tmp nella macchina virtuale. La cronologia viene pertanto cancellata a ogni riavvio. Per ottenere un record permanente della cronologia dei processi, configurare la macchina virtuale come contesto di calcolo in Azure Machine Learning, quindi inviare il processo ad Azure Machine Learning selezionando la macchina virtuale come contesto di calcolo.