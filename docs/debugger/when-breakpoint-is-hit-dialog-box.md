---
title: Finestra di dialogo quando il punto di interruzione viene raggiunto | Microsoft Docs
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
ms.openlocfilehash: 53b19f4dd0d4b0cb97bb33e4895f36c4dc8f670c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728136"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Finestra di dialogo Quando il punto di interruzione viene raggiunto
Con questa finestra di dialogo è possibile personalizzare l'azione che si verifica quando viene raggiunto un punto di interruzione.

## <a name="uielement-list"></a>Elenco UIElement
 **Stampa un messaggio** Stampa un messaggio usando la sintassi DebuggerDisplay. Per ulteriori informazioni, vedere [utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

 Questa casella di testo supporta anche parole chiave speciali, ad esempio $ADDRESS, che possono essere usate da soli o tra parentesi graffe di un'espressione DebuggerDisplay. Le parole chiave disponibili sono elencate nella finestra di dialogo.

 **Continua esecuzione** Questo controllo è abilitato solo quando è selezionata **l'opzione stampa un messaggio** . Con questo controllo selezionato, è possibile usare un punto di interruzione come punto di analisi per tracciare l'esecuzione del programma, anziché interferire quando viene raggiunto il percorso.

## <a name="see-also"></a>Vedere anche
- [Uso di punti di interruzione](../debugger/using-breakpoints.md)
- [Uso dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)