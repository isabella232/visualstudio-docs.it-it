---
title: Attività GPU (questo processo) | Microsoft Docs
description: Leggere le informazioni sui segmenti di attività GPU (questo processo) nella visualizzazione thread del Visualizzatore di concorrenza.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bdb39504cae42e943de1864d8edc308b96e0e742
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878136"
---
# <a name="gpu-activity-this-process"></a>Attività GPU (questo processo)
I segmenti **Attività GPU (questo processo)** nella visualizzazione Thread nel visualizzatore di concorrenza rappresentano i casi in cui la GPU stava eseguendo l'elaborazione delle richieste per conto del processo corrente. Queste richieste vengono inviate alla GPU come pacchetti di accesso diretto alla memoria (DMA). La lunghezza di un segmento rappresenta l'intervallo di tempo per cui la GPU ha elaborato un pacchetto DMA per conto del processo corrente.

 Quando si seleziona il segmento di attività GPU, il rapporto nella scheda **Corrente** visualizza le informazioni sul pacchetto DMA che è stato elaborato. Queste informazioni includono la quantità di tempo per cui il pacchetto è rimasto in attesa nella coda hardware associata al motore di DirectX, il processo che ha inviato il pacchetto e il tempo richiesto per elaborare il pacchetto. Un processo diverso dal processo corrente può avere inviato fisicamente il pacchetto DMA alla GPU. Il visualizzatore di concorrenza è in grado di rilevare quando un altro processo ha inviato operazioni alla GPU per conto del processo corrente.