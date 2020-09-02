---
title: Contesto di valutazione dell'espressione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377609cb9f971b667872c198a53b45a6288f2c15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152787"
---
# <a name="expression-evaluation-context"></a>Contesto di valutazione delle espressioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debug, un **contesto di valutazione dell'espressione**:  
  
- Rappresenta un contesto per la valutazione dell'espressione. In genere, un contesto di valutazione corrisponde all'ambito lessicale in cui valutare variabili, parametri, funzioni e metodi. Ad esempio, un contesto di valutazione dell'espressione associato a un stack frame fornirà il contesto per la valutazione di variabili locali, parametri di metodo e membri di classe (se applicabile).  
  
- Esiste quando un programma è stato interrotto in corrispondenza di un punto di interruzione. L'espressione stessa è una struttura di dati che rappresenta un'espressione analizzata pronta per l'associazione e la valutazione all'interno del contesto specificato.  
  
     In modo più dettagliato, le espressioni vengono create usando il metodo [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . Quando viene valutata un'espressione, viene generata una stringa stampabile contenente il nome e il tipo di variabile o argomento e il relativo valore. Questa stringa viene visualizzata nella finestra Espressioni di controllo o nella finestra variabili locali dell'IDE.  
  
     Dato un oggetto `BSTR` e un'interfaccia [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) , un motore di debug (de) può creare un'interfaccia [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) analizzando un'espressione. Data un' `IDebugExpression2` interfaccia, il de può ottenere un valore tramite la valutazione di espressioni sincrone o asincrone. Questo valore, insieme al nome e al tipo della variabile o dell'argomento, viene inviato all'IDE per la visualizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di valutazione delle espressioni](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
