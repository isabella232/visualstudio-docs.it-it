---
title: Visualizzazione dei processi recenti
description: Dopo aver inviato i processi, è possibile visualizzare l'elenco dei processi per visualizzarne lo stato, la durata e altro ancora.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-ai-tools
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 6377acf831db6ce7f14a2a3e7605f01777f49496
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633371"
---
# <a name="view-recent-job-performance-and-details"></a>Visualizzare le prestazioni e i dettagli di processi recenti

Dopo l'invio dei processi è possibile visualizzare l'elenco dei processi per controllare il relativo stato, la durata e altri dettagli.

1. **Nell'Esplora server** espandere il contesto di calcolo specifico.
2. Fare doppio clic su **Processi**.
3. Verrà visualizzato l'elenco dei processi inviati a tale contesto di calcolo.
4. Selezionare un processo **specifico nell'elenco** per visualizzare i dettagli.

![Monitorare i processi](media/job-details/monitor-jobs.png)

> La cronologia dei processi inviati alle macchine virtuali di Linux viene archiviata nella directory /tmp nella macchina virtuale. La cronologia viene pertanto cancellata a ogni riavvio. Per ottenere un record permanente della cronologia dei processi, configurare la macchina virtuale come contesto di calcolo in Azure Machine Learning, quindi inviare il processo ad Azure Machine Learning selezionando la macchina virtuale come contesto di calcolo.
