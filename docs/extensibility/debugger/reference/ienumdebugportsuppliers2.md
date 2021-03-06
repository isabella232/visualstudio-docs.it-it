---
description: Questa interfaccia enumera i fornitori di porte.
title: IEnumDebugPortSuppliers2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 893135291be3126055fa139dacaf3cc12141d8f4
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224486"
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
 La tabella seguente illustra i metodi di `IEnumDebugPortSuppliers2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Recupera un numero specificato di fornitori di porte in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Ignora un numero specificato di fornitori di porte in una sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Ottiene il numero di fornitori di porte in un enumeratore.|

## <a name="remarks"></a>Commenti
 In genere non è necessario che un motore di debug ottenga questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
