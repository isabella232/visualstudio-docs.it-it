---
title: IEnumDebugPortSuppliers2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39d9d9462fe1951f01927b9180fa8a99aee535be
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326387"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Questa interfaccia enumera i fornitori di porte.

## <a name="syntax"></a>Sintassi

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa questa interfaccia per rappresentare un elenco di fornitori di porte.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) per ottenere un elenco di fornitori di porte.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugPortSuppliers2`.

|Metodo|Descrizione|
|------------|-----------------|
|[avanti](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Recupera un determinato numero di fornitori di porte in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Ignora un determinato numero di fornitori di porte in una sequenza di enumerazione.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Ottiene il numero di fornitori di porte in un enumeratore.|

## <a name="remarks"></a>Note
 Un motore di debug non è in genere necessario ottenere questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)