---
title: Attività GPU (altri processi) | Microsoft Docs
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
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d988ab3e381ef8c5d25eed1978eed39c53e9e24
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49272142"
---
# <a name="gpu-activity-other-processes"></a>Attività GPU (altri processi)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I segmenti **Attività GPU (altri processi)** nella visualizzazione Thread del visualizzatore di concorrenza rappresentano i casi in cui la GPU stava eseguendo l'elaborazione delle richieste per conto di altri processi nel sistema. Queste richieste vengono inviate alla GPU come pacchetti di accesso diretto alla memoria (DMA).  La lunghezza di un segmento rappresenta l'intervallo di tempo per cui il pacchetto è stato elaborato dalla GPU.  
  
 Quando si seleziona questo tipo di segmento, il rapporto nella scheda **Corrente** visualizza le informazioni sul pacchetto che è stato elaborato.  Le informazioni includono la quantità di tempo per cui il pacchetto è rimasto in attesa nella coda hardware associata al motore di DirectX, il processo che ha inviato il pacchetto e il tempo richiesto per elaborare il pacchetto.



