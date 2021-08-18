---
title: Oggetto IDebugExpressionContext2 | Microsoft Docs
description: Questa interfaccia rappresenta un contesto per la valutazione delle espressioni
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 01d5c04d8314bcf81f1a7d3e42ddf4d4517956d3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064227"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Questa interfaccia rappresenta un contesto per la valutazione dell'espressione.

## <a name="syntax"></a>Sintassi

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per rappresentare un contesto in cui un'espressione può essere valutata.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [GetExpressionContext restituisce](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) l'interfaccia this. Questa interfaccia è accessibile solo quando il programma in fase di debug è stato sospeso ed è stack frame disponibile un'interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugExpressionContext2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Recupera il nome del contesto di valutazione.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analizza un'espressione basata su testo per la valutazione.|

## <a name="remarks"></a>Commenti
 Un contesto di valutazione può essere pensato come un ambito per l'esecuzione della valutazione delle espressioni.

 Quando un programma si arresta, gestione debug sessione (SDM) ottiene un stack frame da DE con una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). SDM chiama quindi [GetExpressionContext per](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) ottenere l'interfaccia `IDebugExpressionContext2` . Questa operazione è seguita da una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per creare [un'interfaccia IDebugExpression2,](../../../extensibility/debugger/reference/idebugexpression2.md) che rappresenta l'espressione analizzata pronta per la valutazione.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
