---
title: Quando punto di interruzione è nella finestra di dialogo Hit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4cc3c2366ca20328f591b0661e8c2b3e5af1e45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929199"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Finestra di dialogo Quando il punto di interruzione viene raggiunto
Con questa finestra di dialogo, è possibile personalizzare l'azione che si verifica quando viene raggiunto un punto di interruzione.

## <a name="uielement-list"></a>Elenco UIElement
 **Stampa un messaggio** viene stampato un messaggio, utilizzando la sintassi DebuggerDisplay. Per altre informazioni, vedere [usando l'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

 Questa casella di testo supporta anche la parole chiave speciali (ad esempio $ADDRESS) che possono essere utilizzate da soli o all'interno di parentesi graffe in un'espressione DebuggerDisplay. Le parole chiave disponibili sono elencate nella finestra di dialogo.

 **L'esecuzione continua** questo controllo è abilitato solo quando **stampano un messaggio** sia selezionata. Questo controllo è selezionata, è possibile usare un punto di interruzione come un punto di analisi per tracciare l'esecuzione del programma, invece di interruzione quando viene raggiunto il percorso.

## <a name="see-also"></a>Vedere anche
- [Uso di punti di interruzione](../debugger/using-breakpoints.md)
- [Uso dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)