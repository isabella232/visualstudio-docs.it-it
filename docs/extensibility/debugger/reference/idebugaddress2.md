---
title: Proprietà IDebugAddress2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 402d8c8bcb50c570ff680b8fe1cf8d26f037ba17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736561"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Questa interfaccia fornisce l'accesso all'ID del processo proprietario dell'oggetto il cui indirizzo è rappresentato da questa interfaccia.

## <a name="syntax"></a>Sintassi

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa il [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia. Questa interfaccia fornisce l'accesso all'ID del processo proprietario dell'oggetto correlato a questo indirizzo.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Utilizzare [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia dal [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi in vtable Order
 Oltre ai metodi ereditati dal IDebugAddress interfaccia, questa interfaccia implementa il metodo seguente:In addition to the methods inherited from the [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface, this interface implements the following method:

|Metodo|Descrizione|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Recupera l'ID del processo proprietario dell'oggetto rappresentato da questa interfaccia.|

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
