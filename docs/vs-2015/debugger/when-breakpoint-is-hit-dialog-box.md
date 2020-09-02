---
title: Finestra di dialogo quando il punto di interruzione viene raggiunto | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149413"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Finestra di dialogo Quando il punto di interruzione viene raggiunto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con questa finestra di dialogo è possibile personalizzare l'azione che si verifica quando viene raggiunto un punto di interruzione.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **Stampa un messaggio**  
 Stampa un messaggio usando la sintassi DebuggerDisplay. Per ulteriori informazioni, vedere [utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Questa casella di testo supporta anche parole chiave speciali, ad esempio $ADDRESS, che possono essere usate da soli o tra parentesi graffe di un'espressione DebuggerDisplay. Le parole chiave disponibili sono elencate nella finestra di dialogo.  
  
 **Continua esecuzione**  
 Questo controllo è attivato solo quando è selezionata l'opzione **Stampa un messaggio**. Con questo controllo selezionato, è possibile usare un punto di interruzione come punto di analisi per tracciare l'esecuzione del programma, anziché interferire quando viene raggiunto il percorso.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di punti di interruzione](../debugger/using-breakpoints.md)   
 [Utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
