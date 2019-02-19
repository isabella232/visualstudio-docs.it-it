---
title: Tempo di gestione della memoria | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48cbdd523f4527af84c52366a439a18330e1828c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54752061"
---
# <a name="memory-management-time"></a>Tempo di gestione della memoria
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questi segmenti nella sequenza temporale sono associati a tempi di blocco categorizzati come gestione della memoria. Ciò implica che un thread è bloccato da un evento associato a un'operazione di gestione della memoria quale il paging. Durante questo periodo, un thread è stato bloccato in un'API o in uno stato del kernel che il visualizzatore di concorrenza calcola come gestione della memoria. Si tratta di eventi come il paging e l'allocazione di memoria.  
  
 Esaminare gli stack di chiamate e i rapporti di profilo associati per comprendere meglio i motivi alla base della categorizzazione dei blocchi come gestione della memoria.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)
