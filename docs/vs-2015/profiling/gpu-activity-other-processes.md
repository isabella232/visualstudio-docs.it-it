---
title: Attività GPU (altri processi) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3b0e97d82d67916aa71f932038930dba48c17e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62434137"
---
# <a name="gpu-activity-other-processes"></a>Attività GPU (altri processi)
I segmenti **Attività GPU (altri processi)** nella visualizzazione Thread del visualizzatore di concorrenza rappresentano i casi in cui la GPU stava eseguendo l'elaborazione delle richieste per conto di altri processi nel sistema. Queste richieste vengono inviate alla GPU come pacchetti di accesso diretto alla memoria (DMA).  La lunghezza di un segmento rappresenta l'intervallo di tempo per cui il pacchetto è stato elaborato dalla GPU.

 Quando si seleziona questo tipo di segmento, il rapporto nella scheda **Corrente** visualizza le informazioni sul pacchetto che è stato elaborato.  Le informazioni includono la quantità di tempo per cui il pacchetto è rimasto in attesa nella coda hardware associata al motore di DirectX, il processo che ha inviato il pacchetto e il tempo richiesto per elaborare il pacchetto.