---
title: Chiamata di eventi del debugger | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146392"
---
# <a name="calling-debugger-events"></a>Chiamata degli eventi del debugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gli eventi nelle sessioni di debug si verificano in un ordine specifico.  
  
## <a name="discussion"></a>Discussione  
 Per comprendere il modello di chiamate tra il motore di debug (DE) e la gestione del debug della sessione (SDM), l'esempio seguente rappresenta l'ordine chiamante degli eventi che si verificano in una sessione di debug tipica:  
  
1. [Collegamento e scollegamento di un programma](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2. [Avvio del debugger](../../extensibility/debugger/launching-the-debugger.md)  
  
3. [Terminazione di un programma](../../extensibility/debugger/terminating-a-program.md)  
  
4. [Creazione di un punto di interruzione](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5. [Quando un punto di interruzione viene associato o diventa non associato](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6. [Errori del punto di interruzione](../../extensibility/debugger/breakpoint-errors.md)  
  
7. [Raggiungimento di un punto di interruzione](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8. [Eliminazione di un punto di interruzione](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Immissione della modalità di interruzioni](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Esecuzione in modalità di interruzioni](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Valutazione delle espressioni in modalità di interruzioni](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Gestione delle eccezioni](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)
