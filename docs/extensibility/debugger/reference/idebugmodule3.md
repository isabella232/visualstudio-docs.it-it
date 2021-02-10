---
title: IDebugModule3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa655c03665c9eed54feabc5af679765b09ac0a6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955522"
---
# <a name="idebugmodule3"></a>IDebugModule3
Questa interfaccia rappresenta un modulo che supporta percorsi alternativi di simboli e Stati JustMyCode.

## <a name="syntax"></a>Sintassi

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per supportare percorsi alternativi di simboli e per lavorare con gli Stati JustMyCode (vedere il [Glossario del debugger di Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) per una definizione di "justMyCode").

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) restituisce questa interfaccia. Il DE invia l'interfaccia [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) al gestore di debug della sessione (SDM) usando il metodo dell' [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) . Inoltre, una chiamata a [QueryInterface](/cpp/atl/queryinterface) su un'interfaccia [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) restituisce questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi sull'interfaccia [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Restituisce un elenco di percorsi in cui vengono cercati i simboli e i risultati della ricerca in ogni percorso.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Carica e inizializza i simboli per il modulo corrente.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Restituisce un flag che specifica se il modulo rappresenta il codice utente.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Specifica se il modulo deve essere considerato o meno il codice utente.|

## <a name="remarks"></a>Commenti
 Visual Studio è il consumer tipico di questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
