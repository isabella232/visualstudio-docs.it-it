---
title: Contesto di valutazione dell'espressione | Microsoft Docs
description: Informazioni sul contesto di valutazione delle espressioni, che rappresenta un contesto per la valutazione delle espressioni ed esiste quando un programma è stato interrotto in corrispondenza di un punto di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 127746b06ef09496ef8f50aa874ff32e2f983f65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921545"
---
# <a name="expression-evaluation-context"></a>Contesto di valutazione dell'espressione
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, un **contesto di valutazione dell'espressione**:

- Rappresenta un contesto per la valutazione dell'espressione. In genere, un contesto di valutazione corrisponde all'ambito lessicale in cui valutare variabili, parametri, funzioni e metodi. Ad esempio, un contesto di valutazione dell'espressione associato a un stack frame fornirà il contesto per la valutazione di variabili locali, parametri di metodo e membri di classe (se applicabile).

- Esiste quando un programma è stato interrotto in corrispondenza di un punto di interruzione. L'espressione stessa è una struttura di dati che rappresenta un'espressione analizzata pronta per l'associazione e la valutazione all'interno del contesto specificato.

     In modo più dettagliato, le espressioni vengono create usando il metodo [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . Quando viene valutata un'espressione, viene generata una stringa stampabile contenente il nome e il tipo di variabile o argomento e il relativo valore. Questa stringa viene visualizzata nella finestra Espressioni di controllo o nella finestra variabili locali dell'IDE.

     Dato un oggetto `BSTR` e un'interfaccia [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) , un motore di debug (de) può creare un'interfaccia [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) analizzando un'espressione. Data un' `IDebugExpression2` interfaccia, il de può ottenere un valore tramite la valutazione di espressioni sincrone o asincrone. Questo valore, insieme al nome e al tipo della variabile o dell'argomento, viene inviato all'IDE per la visualizzazione.

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
