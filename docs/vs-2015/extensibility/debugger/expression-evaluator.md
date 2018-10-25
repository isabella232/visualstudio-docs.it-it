---
title: Analizzatore di espressioni | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d5ad6c3c97fc88ef938caaccad1627dbc5859c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911908"
---
# <a name="expression-evaluator"></a>Analizzatore di espressioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Analizzatori di espressioni (EE), esaminare la sintassi di una lingua per analizzare e valutare variabili ed espressioni in fase di esecuzione, consentendo loro di essere visualizzato dall'utente quando l'IDE è in modalità di interruzione.  
  
## <a name="using-expression-evaluators"></a>Usando gli analizzatori di espressioni  
 Le espressioni vengono create usando il [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) (metodo), come indicato di seguito:  
  
1. Il motore di debug (DE) implementa il [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia.  
  
2. Ottiene il pacchetto di debug un' `IDebugExpressionContext2` dell'oggetto da un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia e quindi chiama il `IDebugStackFrame2::ParseText` metodo su di essa per ottenere un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto.  
  
3. Le chiamate di debug del pacchetto di [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) metodo o il [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metodo per ottenere il valore dell'espressione. `IDebugExpression2::EvaluateAsync` viene chiamato dalla finestra di comando/controllo immediato. Tutti gli altri componenti dell'interfaccia utente chiamano `IDebugExpression2::EvaluateSync`.  
  
4. Il risultato della valutazione dell'espressione è un' [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che contiene il nome, tipo e valore del risultato della valutazione dell'espressione.  
  
   Durante la valutazione dell'espressione, l'analizzatore di Espressioni richiede informazioni dal componente di provider di simboli. Il provider di simboli fornisce le informazioni sui simboli usate per identificare e comprendere l'espressione analizzata.  
  
   Una volta completata la valutazione dell'espressione asincrona, viene inviato un evento asincrono per la Germania tramite Gestore di sessione di debug (SDM) per notificare all'IDE che la valutazione dell'espressione è stata completata. Una volta completata la valutazione dell'espressione sincrona, il risultato della valutazione viene restituito dalla chiamata al `IDebugExpression2::EvaluateSync` (metodo).  
  
## <a name="implementation-notes"></a>Note di implementazione  
 Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] motori di debug che prevede di comunicare con l'analizzatore di espressioni utilizzando le interfacce di Common Language Runtime (CLR). Di conseguenza, un analizzatore di espressioni che interagisce con il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] motori di debug devono supportare Common Language Runtime (un elenco completo di tutte le interfacce di debug di CLR è reperibile in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)]).  
  
## <a name="see-also"></a>Vedere anche  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)

