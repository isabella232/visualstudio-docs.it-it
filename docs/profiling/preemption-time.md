---
title: Periodo di precedenza | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ac7152ec663a0a7b7bbbeee5c30a38885623cb9
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254759"
---
# <a name="preemption-time"></a>Periodo di precedenza
Questi segmenti nella sequenza temporale sono associati al periodo di blocco categorizzato come Precedenza. Questa categoria implica che un thread viene disattivato per uno dei motivi seguenti:  
  
-   L'utilità di pianificazione lo ha sostituito con un thread con priorità maggiore.  
  
-   Il quantum di esecuzione del thread è scaduto e altri thread erano pronti per l'esecuzione.  
  
 Durante questo periodo, un thread è stato bloccato per un motivo di attesa del kernel che il visualizzatore di concorrenza conteggia come Precedenza. I segmenti con precedenza iniziano quando un thread viene escluso da un core logico e terminano quando tale thread riprende l'esecuzione.  
  
 La descrizione comando per un segmento con precedenza visualizza il nome del processo o del thread che ha causato la precedenza. Tuttavia, ciò non implica che il processo o il thread con precedenza sia stato effettivamente eseguito per tutto il periodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)