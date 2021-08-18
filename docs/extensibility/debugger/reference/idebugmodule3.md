---
description: Questa interfaccia rappresenta un modulo che supporta posizioni alternative di simboli e stati JustMyCode.
title: IDebugModule3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 11b6db77e947ae8cb2ace6353b3f55aa8db48664
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078843"
---
# <a name="idebugmodule3"></a>IDebugModule3
Questa interfaccia rappresenta un modulo che supporta posizioni alternative di simboli e stati JustMyCode.

## <a name="syntax"></a>Sintassi

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per supportare percorsi alternativi di simboli e per usare gli stati JustMyCode (vedere il [glossario](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) del debugger di Visual Studio per una definizione di "JustMyCode").

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [GetSymbolSearchInfo restituisce](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) questa interfaccia. DE invia [l'interfaccia IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) alla gestione del debug di sessione (SDM) usando il [metodo Event.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Inoltre, una chiamata a [QueryInterface](/cpp/atl/queryinterface) su [un'interfaccia IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) restituisce questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi [nell'interfaccia IDebugModule2,](../../../extensibility/debugger/reference/idebugmodule2.md) questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Restituisce un elenco di percorsi cercati per i simboli e i risultati della ricerca in ogni percorso.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Carica e inizializza i simboli per il modulo corrente.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Restituisce il flag che specifica se il modulo rappresenta il codice utente.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Specifica se il modulo deve essere considerato o meno codice utente.|

## <a name="remarks"></a>Commenti
 Visual Studio è il consumer tipico di questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
