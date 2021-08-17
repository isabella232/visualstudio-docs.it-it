---
description: Questa interfaccia registra o annulla la registrazione di un programma di cui è possibile eseguire il debug con la porta su cui è in esecuzione.
title: IDebugPortNotify2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 380592c15a0644fe64ab1e3f68fdd9ab0ec7d9d9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088211"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Questa interfaccia registra o annulla la registrazione di un programma di cui è possibile eseguire il debug con la porta su cui è in esecuzione.

## <a name="syntax"></a>Sintassi

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia per supportare l'aggiunta e la rimozione di programmi dalla porta. Viene in genere implementato nello stesso oggetto che implementa [l'interfaccia IDebugPort2.](../../../extensibility/debugger/reference/idebugport2.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [QueryInterface](/cpp/atl/queryinterface) `IDebugPort2` sull'interfaccia restituisce questa interfaccia. Inoltre, una chiamata a [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) restituisce questa interfaccia. Un motore di debug può visualizzare questa interfaccia come parametro [di WatchForProviderEvents.](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugPortNotify2` .

|Metodo|Descrizione|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registra un programma di cui è possibile eseguire il debug con la porta su cui è in esecuzione.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Annulla la registrazione di un programma di cui è possibile eseguire il debug dalla porta su cui è in esecuzione.|

## <a name="remarks"></a>Commenti
 A meno che una porta di debug non sia in grado di sapere quando i programmi vengono caricati o scaricati, un fornitore di porte personalizzato deve implementare questa interfaccia. Tutti i programmi caricati per il debug tramite una determinata porta vengono monitorati tramite questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
