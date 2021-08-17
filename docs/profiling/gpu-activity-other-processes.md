---
title: Attività GPU (altri processi) | Microsoft Docs
description: Informazioni sui segmenti attività GPU (altri processi) nella visualizzazione Thread del visualizzatore di concorrenza.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 88bae242a814b283fd6dc91170c3a81c0cd126f7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033720"
---
# <a name="gpu-activity-other-processes"></a>Attività GPU (altri processi)
I segmenti **Attività GPU (altri processi)** nella visualizzazione Thread del visualizzatore di concorrenza rappresentano i casi in cui la GPU stava eseguendo l'elaborazione delle richieste per conto di altri processi nel sistema. Queste richieste vengono inviate alla GPU come pacchetti di accesso diretto alla memoria (DMA).  La lunghezza di un segmento rappresenta l'intervallo di tempo per cui il pacchetto è stato elaborato dalla GPU.

 Quando si seleziona questo tipo di segmento, il rapporto nella scheda **Corrente** visualizza le informazioni sul pacchetto che è stato elaborato.  Le informazioni includono la quantità di tempo per cui il pacchetto è rimasto in attesa nella coda hardware associata al motore di DirectX, il processo che ha inviato il pacchetto e il tempo richiesto per elaborare il pacchetto.