---
title: La chiamata a eventi del Debugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f162affe2324afaa8fb1d506c3177311386bfc1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146392"
---
# <a name="calling-debugger-events"></a>Chiamata degli eventi del debugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gli eventi nella sessione di debug e si verificano in un ordine specifico.  
  
## <a name="discussion"></a>Discussione  
 Per comprendere il criterio di chiamate tra il motore di debug (DE) e la gestione di debug di sessione (SDM), di seguito rappresenta l'ordine di chiamata degli eventi che si verificano durante una normale sessione di debug:  
  
1. [Collegamento e scollegamento da un programma](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2. [L'avvio del debugger](../../extensibility/debugger/launching-the-debugger.md)  
  
3. [Terminazione di un programma](../../extensibility/debugger/terminating-a-program.md)  
  
4. [Creazione di un punto di interruzione](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5. [Quando si associa un punto di interruzione o diventare non associato](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6. [Errori di punto di interruzione](../../extensibility/debugger/breakpoint-errors.md)  
  
7. [Raggiungere un punto di interruzione](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8. [L'eliminazione di un punto di interruzione](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Modalità di interruzione](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Esecuzione di istruzioni in modalità di interruzione](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Valutazione dell'espressione in modalità di interruzione](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Gestione delle eccezioni](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)
