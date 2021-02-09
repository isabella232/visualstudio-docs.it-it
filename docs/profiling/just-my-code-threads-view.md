---
title: Just My Code (visualizzazione dei thread) | Microsoft Docs
description: Viene illustrato come filtrare lo stack di chiamate per visualizzare solo il codice più un livello di funzioni chiamate se si seleziona l'opzione Just My Code.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.jmc
helpviewer_keywords:
- Concurrency Visualizer, Just My Code (Threads View)
ms.assetid: a9ac8a2c-9d99-4207-8ed4-e87f033f440d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f09b3e0837adf9490e9c10c81f18ff9fc9c5573e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918044"
---
# <a name="just-my-code-threads-view"></a>Just My Code (Visualizzazione thread)
Se si seleziona questa opzione, lo stack di chiamate verrà filtrato per mostrare solo il codice più un livello di funzioni chiamate attraverso lo stack di chiamate.

 Attivando questa opzione, è possibile ridurre significativamente la complessità dello stack di chiamate e probabilmente semplificare la diagnosi di un problema specifico.

 In alcuni casi, selezionando questa opzione la chiamata all'origine del blocco potrebbe risultare esclusa. Se sono necessari i dettagli dello stack di chiamate completo per determinare le cause, deselezionare questa opzione per esporre lo stack di chiamate completo.

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)
- [Percentuale di riduzione del rumore](../profiling/noise-reduction-percentage.md)