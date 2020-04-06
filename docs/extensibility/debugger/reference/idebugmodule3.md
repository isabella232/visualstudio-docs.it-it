---
title: Proprietà IDebugModule3 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84db1b672a9460ef3809162a2a1433f269796046
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726739"
---
# <a name="idebugmodule3"></a>IDebugModule3
Questa interfaccia rappresenta un modulo che supporta posizioni alternative di simboli e JustMyCode stati.

## <a name="syntax"></a>Sintassi

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per supportare posizioni alternative di simboli e per utilizzare gli stati JustMyCode (vedere il [Glossario del debugger](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) di Visual Studio per una definizione di "JustMyCode").

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) restituisce questa interfaccia. Il DE invia il [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) interfaccia al gestore di sessione di debug (SDM) utilizzando il [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metodo. Inoltre, una chiamata a [QueryInterface](/cpp/atl/queryinterface) su un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interfaccia restituisce questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi sul IDebugModule2 interfaccia, questa interfaccia implementa i metodi seguenti:In addition to the methods on the [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interface, this interface implements the following methods:

|Metodo|Descrizione|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Restituisce un elenco di percorsi cercati per i simboli e i risultati della ricerca di ogni percorso.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Carica e inizializza i simboli per il modulo corrente.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Restituisce un flag che specifica se il modulo rappresenta il codice utente.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Specifica se il modulo deve essere considerato codice utente o meno.|

## <a name="remarks"></a>Osservazioni
 Visual Studio è il consumer tipico di questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
