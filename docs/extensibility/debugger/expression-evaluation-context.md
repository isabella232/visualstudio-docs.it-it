---
title: Contesto di valutazione dell'espressione Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e939a4fa5f4673e2f701206c96599c54bc0c3b51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738743"
---
# <a name="expression-evaluation-context"></a>Contesto di valutazione dell'espressione
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, un contesto di **valutazione dell'espressione:**

- Rappresenta un contesto per la valutazione dell'espressione. In genere, un contesto di valutazione corrisponde all'ambito lessicale all'interno del quale valutare variabili, parametri, funzioni e metodi. Ad esempio, un contesto di valutazione dell'espressione associato a uno stack frame fornirà il contesto per la valutazione di variabili locali, parametri di metodo e membri di classe (se applicabile).

- Esiste quando un programma è stato arrestato in corrispondenza di un punto di interruzione. L'espressione stessa è una struttura di dati che rappresenta un'espressione analizzata pronta per l'associazione e la valutazione all'interno del contesto specificato.

     In modo più dettagliato, le espressioni vengono create utilizzando il [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metodo. Quando un'espressione viene valutata, genera una stringa stampabile contenente il nome e il tipo della variabile o dell'argomento e il relativo valore. Questa stringa viene visualizzata nella finestra Espressioni di controllo o nella finestra Variabili locali dell'IDE.

     Dato `BSTR` un e un [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia, un motore di debug (DE) può creare un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia analizzando un'espressione. Dato `IDebugExpression2` un'interfaccia, il DE può ottenere un valore tramite la valutazione sincrona o asincrona dell'espressione. Questo valore, insieme al nome e al tipo della variabile o dell'argomento, viene inviato all'IDE per la visualizzazione.

## <a name="see-also"></a>Vedere anche
- [Interfacce di valutazione delle espressioni](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Contesti del debuggerDebugger contexts](../../extensibility/debugger/debugger-contexts.md)
