---
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b664b068ac7cd30a7475ab14bfe1b064c98142c2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324399"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Questa interfaccia enumera [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) strutture.

## <a name="syntax"></a>Sintassi

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia come parte del supporto per i riferimenti agli oggetti in memoria. Questa interfaccia deve essere implementata solo se i riferimenti sono supportati.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Le chiamate di Visual Studio [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugReferenceInfo2`.

|Metodo|Descrizione|
|------------|-----------------|
|[avanti](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Recupera un numero specificato di [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) strutture in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Ignora un numero specificato di [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) strutture nella sequenza di enumerazione.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Ottiene il numero di [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) strutture nell'enumeratore.|

## <a name="remarks"></a>Note
 Un riferimento è essenzialmente un tipo e un indirizzo, mentre una proprietà è un nome, tipo e l'indirizzo. Un riferimento viene mantenuto fino a quando l'oggetto indicato è presente in memoria. Visualizzare [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) per altri dettagli.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)