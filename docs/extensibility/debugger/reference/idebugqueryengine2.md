---
description: Questa interfaccia consente al gestore di debug della sessione (SDM) di recuperare un'interfaccia che rappresenta il motore di debug .
title: IDebugQueryEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: bf399a8ccf018e8e18c18ba0af2b54a0e5b948c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029866"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Questa interfaccia consente al gestore di debug della sessione (SDM) di recuperare un'interfaccia che rappresenta il motore di debug .

## <a name="syntax"></a>Sintassi

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 DE implementa questa interfaccia sugli oggetti che implementano le interfacce DE più comuni (ad esempio [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)e [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) per consentire l'accesso all'interfaccia [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) del de stesso.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un'interfaccia DE tipica per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugQueryEngine2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Ottiene un'interfaccia del motore di debug personalizzato.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene in genere implementata nell'oggetto che implementa [l'interfaccia IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) per supportare l'esecuzione delle funzioni ordinate in base alla causalità. ciò significa che quando il debugger esce da una funzione, la funzione successiva da eseguire potrebbe non essere la funzione precedente nello stack, ma una funzione in un altro thread. Per una definizione di "causalità", vedere il [glossario Visual Studio Debugger](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
