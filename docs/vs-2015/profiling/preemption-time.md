---
title: Periodo di precedenza | Microsoft Docs
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
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e1ddd0f239317021d38017ec159de46ecbc2aa77
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721405"
---
# <a name="preemption-time"></a>Tempo di annullamento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questi segmenti nella sequenza temporale sono associati al periodo di blocco categorizzato come Precedenza. Questa categoria implica che un thread viene disattivato per uno dei motivi seguenti:  
  
- L'utilità di pianificazione lo ha sostituito con un thread con priorità maggiore.  
  
- Il quantum di esecuzione del thread è scaduto e altri thread erano pronti per l'esecuzione.  
  
  Durante questo periodo, un thread è stato bloccato per un motivo di attesa del kernel che il visualizzatore di concorrenza conteggia come Precedenza. I segmenti con precedenza iniziano quando un thread viene escluso da un core logico e terminano quando tale thread riprende l'esecuzione.  
  
  La descrizione comando per un segmento con precedenza visualizza il nome del processo o del thread che ha causato il superamento. Tuttavia, ciò non implica che il processo o il thread con precedenza sia stato effettivamente eseguito per tutto il periodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)



