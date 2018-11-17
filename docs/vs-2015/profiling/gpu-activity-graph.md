---
title: Grafico Attività GPU | Microsoft Docs
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
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38ba74ac314710b1202f13373685ddbdda0df0f6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791124"
---
# <a name="gpu-activity-graph"></a>Grafico dell'attività GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il grafico Attività GPU nel visualizzatore di concorrenza visualizza il livello di attività di DirectX nel sistema, misurato in base al numero dei motori di DirectX usati nel tempo.  Il grafico non mostra gli specifici motori usati.  Un motore viene considerato in uso se sta elaborando una qualsiasi operazione GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Colori del grafico Attività GPU  
 Il verde indica l'uso dei motori di DirectX da parte del processo corrente.  
  
 Il grigio chiaro indica l'uso dei motori di DirectX da parte di altri processi nel sistema. Per ridurre l'uso dei motori di DirectX da parte di altri processi, ridurre il numero di altri processi in esecuzione nel sistema.  
  
 Il bianco indica la disponibilità dei motori inutilizzati di DirectX nel sistema. Tali motori sono disponibili per il processo se è possibile trovare ulteriori opportunità per sfruttarli. Alcuni motori possono essere usati solo per tipi specifici di attività.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Utilizzo](../profiling/utilization-view.md)



