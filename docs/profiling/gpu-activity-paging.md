---
title: Attività GPU (paging) | Microsoft Docs
description: Esaminare i segmenti Attività GPU (paging) nella scheda Thread del visualizzatore di concorrenza. I segmenti rappresentano i momenti in cui la GPU stava elaborando le richieste di paging.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f2ec6ebfde3a8f205e3a515c70930a1344598c9b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634372"
---
# <a name="gpu-activity-paging"></a>Attività GPU (paging)
I segmenti **Attività GPU (paging)** nella scheda **Thread** rappresentano i casi in cui la GPU stava eseguendo l'elaborazione delle richieste di paging.  La lunghezza di un segmento rappresenta l'intervallo di tempo per cui la GPU ha elaborato un pacchetto di paging di accesso diretto alla memoria (DMA). In genere, i pacchetti di paging vengono associati al trasferimento di memoria tra la CPU e la GPU.

 Quando si seleziona un segmento di paging GPU, il rapporto nella scheda **Corrente** visualizza le informazioni sul pacchetto DMA che è stato elaborato. Ciò include la quantità di tempo per cui è rimasto in attesa nella coda hardware associata al motore di DirectX, il processo che ha inviato il pacchetto DMA e il tempo richiesto per elaborare il pacchetto.

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Uso](../profiling/utilization-view.md)