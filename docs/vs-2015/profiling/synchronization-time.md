---
title: Periodo di sincronizzazione | Microsoft Docs
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
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12be885a79daa3ba5531f6da9652d6a9708b3c96
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826999"
---
# <a name="synchronization-time"></a>Tempo di sincronizzazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questi segmenti nella sequenza temporale sono associati ai periodi di blocco categorizzati come Sincronizzazione. Quando un thread viene contrassegnato come bloccato durante la sincronizzazione, è implicita una delle cause seguenti:  
  
- L'esecuzione del thread potrebbe aver causato una chiamata a un'API di sincronizzazione dei thread nota, come `EnterCriticalSection()` o `WaitForSingleObject()`.  
  
- L'algoritmo di corrispondenza delle API non può essere del tutto completo e pertanto alcune API che potrebbero essere mappate ad altre categorie possono comparire anche nella categoria Sincronizzazione perché un frame nello stack di chiamate raggiunge una primitiva di blocco del kernel sottostante mappata a questa categoria.  
  
  Per comprendere la causa sottostante a un evento di blocco del thread, esaminare attentamente gli stack di chiamate all'origine del blocco e i report di profilatura.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)



