---
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66fd149bc3eed7633586c156f6493c8febcbeaac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330354"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Questa interfaccia fornisce l'accesso all'ID del processo a cui appartiene l'oggetto il cui indirizzo è rappresentato da questa interfaccia.

## <a name="syntax"></a>Sintassi

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia nello stesso oggetto che implementa il [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia. Questa interfaccia fornisce l'accesso all'ID del processo a cui appartiene l'oggetto correlato a questo indirizzo.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Uso [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia dalle [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable
 Oltre ai metodi ereditati dal [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia, questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Recupera l'ID del processo a cui appartiene l'oggetto rappresentato da questa interfaccia.|

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)