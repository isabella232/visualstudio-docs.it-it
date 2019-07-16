---
title: Quando punto di interruzione è nella finestra di dialogo Hit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a7cd140a22c435df0875c089a69476d3e1e61cf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149413"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Finestra di dialogo Quando il punto di interruzione viene raggiunto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
