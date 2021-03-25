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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e74833768ed1a287c0dcf3b641b858261c2d661
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059183"
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
