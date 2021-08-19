---
description: Questa interfaccia viene usata per rappresentare e ottenere informazioni da un server in un computer in rete.
title: Interfaccia IDebugCoreServer2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ebee42f829a3824477fa5c5e84870ad9a16462bf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119672"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Questa interfaccia viene usata per rappresentare e ottenere informazioni da un server in un computer in rete.

## <a name="syntax"></a>Sintassi

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa questa interfaccia per rappresentare un server. Ogni istanza di Visual Studio crea un'istanza di questa interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Un fornitore di porte personalizzato riceve questa interfaccia in una chiamata [all'evento](../../../extensibility/debugger/reference/idebugportevents2-event.md).

 Un motore di debug può ottenere questa interfaccia indirettamente tramite una chiamata a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (che restituisce [IDebugCoreServer3,](../../../extensibility/debugger/reference/idebugcoreserver3.md)un'interfaccia derivata da `IDebugCoreServer2` ).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugCoreServer2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Ottiene il nome e gli attributi di un computer.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Ottiene il nome di un computer.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Ottiene un fornitore di porte presente in un computer.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Ottiene una porta già esistente in un computer.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Crea un enumeratore per tutte le porte in un computer.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Crea un enumeratore per tutti i fornitori di porte in un computer.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Ottiene le utilità del computer per un computer.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene usata anche da Visual Studio per esplorare i processi in esecuzione nei computer in rete.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
