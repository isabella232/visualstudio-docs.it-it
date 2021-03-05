---
description: Questa interfaccia registra o Annulla la registrazione di un programma di cui è possibile eseguire il debug con la porta su cui è in esecuzione.
title: IDebugPortNotify2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 759be0ff57da7c6bb65ed6ca8191720f835b894a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169340"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Questa interfaccia registra o Annulla la registrazione di un programma di cui è possibile eseguire il debug con la porta su cui è in esecuzione.

## <a name="syntax"></a>Sintassi

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia per supportare l'aggiunta e la rimozione di programmi dalla porta. Viene in genere implementato nello stesso oggetto che implementa l'interfaccia [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) .

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [QueryInterface](/cpp/atl/queryinterface) sull' `IDebugPort2` interfaccia restituisce questa interfaccia. Inoltre, una chiamata a [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) restituisce questa interfaccia. Un motore di debug può vedere questa interfaccia come parametro per [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugPortNotify2` .

|Metodo|Descrizione|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registra un programma di cui è possibile eseguire il debug con la porta su cui è in esecuzione.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Annulla la registrazione di un programma di cui è possibile eseguire il debug dalla porta in cui è in esecuzione.|

## <a name="remarks"></a>Commenti
 A meno che una porta di debug non abbia un modo per stabilire quando i programmi vengono caricati o scaricati, un fornitore di porte personalizzato deve implementare questa interfaccia. Tutti i programmi caricati per il debug tramite una porta specifica vengono rilevati tramite questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
