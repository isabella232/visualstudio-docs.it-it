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
ms.openlocfilehash: 53f27b400c96f6b4336339e8d1beeec0dd87277c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944748"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Finestra di dialogo Quando il punto di interruzione viene raggiunto
Con questa finestra di dialogo, è possibile personalizzare l'azione che si verifica quando viene raggiunto un punto di interruzione.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Stampa un messaggio**  
 Stampa un messaggio, utilizzando la sintassi DebuggerDisplay. Per altre informazioni, vedere [usando l'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Questa casella di testo supporta anche la parole chiave speciali (ad esempio $ADDRESS) che possono essere utilizzate da soli o all'interno di parentesi graffe in un'espressione DebuggerDisplay. Le parole chiave disponibili sono elencate nella finestra di dialogo.  
  
 **Continua esecuzione**  
 Questo controllo è attivato solo quando è selezionata l'opzione **Stampa un messaggio**. Questo controllo è selezionata, è possibile usare un punto di interruzione come un punto di analisi per tracciare l'esecuzione del programma, invece di interruzione quando viene raggiunto il percorso.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di punti di interruzione](../debugger/using-breakpoints.md)   
 [Uso dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)