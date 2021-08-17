---
title: Contesto di valutazione delle espressioni | Microsoft Docs
description: Informazioni sul contesto di valutazione delle espressioni, che rappresenta un contesto per la valutazione delle espressioni ed esiste quando un programma è stato arrestato in corrispondenza di un punto di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4555cf1431b23766085a4174223d3f880d08df45
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089563"
---
# <a name="expression-evaluation-context"></a>Contesto di valutazione dell'espressione
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, un contesto **di valutazione dell'espressione:**

- Rappresenta un contesto per la valutazione dell'espressione. In genere, un contesto di valutazione corrisponde all'ambito lessicale all'interno del quale valutare variabili, parametri, funzioni e metodi. Ad esempio, un contesto di valutazione dell'espressione associato a un stack frame fornirà il contesto per la valutazione di variabili locali, parametri di metodo e membri di classe (se applicabile).

- Esiste quando un programma è stato arrestato in corrispondenza di un punto di interruzione. L'espressione stessa è una struttura di dati che rappresenta un'espressione analizzata pronta per l'associazione e la valutazione all'interno del contesto specificato.

     In modo più dettagliato, le espressioni vengono create usando [il metodo ParseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Quando un'espressione viene valutata, genera una stringa stampabile contenente il nome e il tipo di variabile o argomento e il relativo valore. Questa stringa viene visualizzata nel finestra Espressioni di controllo o nella finestra Variabili locali dell'IDE.

     Dati `BSTR` [un'interfaccia e un'interfaccia IDebugExpressionContext2,](../../extensibility/debugger/reference/idebugexpressioncontext2.md) un motore di debug (DE) può creare [un'interfaccia IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) analizzando un'espressione. Data `IDebugExpression2` un'interfaccia, il de può ottenere un valore tramite la valutazione sincrona o asincrona delle espressioni. Questo valore, insieme al nome e al tipo della variabile o dell'argomento, viene inviato all'IDE per la visualizzazione.

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
