---
title: IDebugModule3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98b506c11ef126d0179b198336e8d969c4eec267
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918647"
---
# <a name="idebugmodule3"></a>IDebugModule3
Questa interfaccia rappresenta un modulo che supporta una posizione alternativa di simboli e JustMyCode stati.

## <a name="syntax"></a>Sintassi

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per supportare le posizioni alternative di simboli e lavorare con gli stati JustMyCode (vedere la [glossario del Debugger di Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) per una definizione di "JustMyCode").

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) restituisce questa interfaccia. L'invia DE il [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) interfaccia per la gestione di debug di sessione (SDM) usando la [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) (metodo). Inoltre, una chiamata a [QueryInterface](/cpp/atl/queryinterface) in un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interfaccia restituisce questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi nel [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interfaccia, questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Restituisce un elenco di percorsi cercati i simboli e i risultati di ogni percorso di ricerca.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Carica e inizializza i simboli per il modulo corrente.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Restituisce flag che specifica se il modulo rappresenta il codice utente.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Specifica se il modulo deve essere considerato codice utente o No.|

## <a name="remarks"></a>Note
 Visual Studio è il consumer tipici di questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)