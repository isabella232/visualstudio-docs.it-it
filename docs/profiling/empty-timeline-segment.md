---
title: Segmento della cronologia vuoto | Microsoft Docs
description: Nel Visualizzatore di concorrenza di Visual Studio comprendere il motivo per cui una sezione di una sequenza temporale può essere vuota (ha uno sfondo bianco) per un tipo di canale.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a4a3265c3b31653d94a686fa8fda12f7699596e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955268"
---
# <a name="empty-timeline-segment"></a>Segmento della sequenza temporale vuoto
Nel visualizzatore di concorrenza, il motivo per cui una sezione della sequenza temporale è vuota (presenta uno sfondo bianco) dipende dal tipo di canale.

- Per un canale di thread di CPU, significa che il thread non esisteva in quella parte della sequenza temporale. Se si è interessati al thread, è possibile trovare la relativa sezione in esecuzione usando il controllo zoom o lo scorrimento orizzontale.

- Per un canale I/O, significa che non si è verificato alcun accesso al disco per conto del processo di destinazione in quel momento.

- Per un canale di DirectX, significa che non è stata eseguita alcuna operazione GPU per conto del processo di destinazione in quella parte della sequenza temporale.

- Per un canale di marcatore, significa che non sono stati generati marcatori.

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)
- [Controllo zoom (visualizzazione thread)](../profiling/zoom-control-threads-view.md)