---
title: Periodo di precedenza | Microsoft Docs
description: Informazioni sul tempo di premption e sul fatto che questi segmenti nella sequenza temporale sono associati al tempo di blocco categorizzato come pre-svuotamento.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 02398447da41c1cb1442c7fb6a10b57625c2ecef
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027448"
---
# <a name="preemption-time"></a>Periodo di precedenza
Questi segmenti nella sequenza temporale sono associati al periodo di blocco categorizzato come Precedenza. Questa categoria implica che un thread viene disattivato per uno dei motivi seguenti:

- L'utilità di pianificazione lo ha sostituito con un thread con priorità maggiore.

- Il quantum di esecuzione del thread è scaduto e altri thread erano pronti per l'esecuzione.

  Durante questo periodo, un thread è stato bloccato per un motivo di attesa del kernel che il visualizzatore di concorrenza conteggia come Precedenza. I segmenti con precedenza iniziano quando un thread viene escluso da un core logico e terminano quando tale thread riprende l'esecuzione.

  La descrizione comando per un segmento con precedenza visualizza il nome del processo o del thread che ha causato la precedenza. Tuttavia, ciò non implica che il processo o il thread con precedenza sia stato effettivamente eseguito per tutto il periodo.

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)