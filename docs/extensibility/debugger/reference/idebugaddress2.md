---
description: Questa interfaccia consente di accedere all'ID del processo a cui appartiene l'oggetto il cui indirizzo è rappresentato da questa interfaccia.
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58a3f01472f60996b7094334de8cb2dbd79acac0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143961"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Questa interfaccia consente di accedere all'ID del processo a cui appartiene l'oggetto il cui indirizzo è rappresentato da questa interfaccia.

## <a name="syntax"></a>Sintassi

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa l'interfaccia [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) . Questa interfaccia consente di accedere all'ID del processo a cui appartiene l'oggetto correlato a questo indirizzo.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Usare [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia dall'interfaccia [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable
 Oltre ai metodi ereditati dall'interfaccia [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) , questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Recupera l'ID del processo a cui appartiene l'oggetto rappresentato da questa interfaccia.|

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
