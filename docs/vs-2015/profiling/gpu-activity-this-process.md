---
title: Attività GPU (questo processo) | Microsoft Docs
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
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1b0949a71dc4db1ee217d691d4aae7928faf301
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751410"
---
# <a name="gpu-activity-this-process"></a>Attività GPU (questo processo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I segmenti **Attività GPU (questo processo)** nella visualizzazione Thread nel visualizzatore di concorrenza rappresentano i casi in cui la GPU stava eseguendo l'elaborazione delle richieste per conto del processo corrente. Queste richieste vengono inviate alla GPU come pacchetti di accesso diretto alla memoria (DMA). La lunghezza di un segmento rappresenta l'intervallo di tempo per cui la GPU ha elaborato un pacchetto DMA per conto del processo corrente.  
  
 Quando si seleziona il segmento di attività GPU, il rapporto nella scheda **Corrente** visualizza le informazioni sul pacchetto DMA che è stato elaborato. Queste informazioni includono la quantità di tempo per cui il pacchetto è rimasto in attesa nella coda hardware associata al motore di DirectX, il processo che ha inviato il pacchetto e il tempo richiesto per elaborare il pacchetto. Un processo diverso dal processo corrente può avere inviato fisicamente il pacchetto DMA alla GPU. Il visualizzatore di concorrenza è in grado di rilevare quando un altro processo ha inviato operazioni alla GPU per conto del processo corrente.



