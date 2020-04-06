---
title: Proprietà IEnumDebugReferenceInfo2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6132235a7e4789c7d9efe5bae9d7fd531112dab4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715273"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Questa interfaccia enumera le strutture [DEBUG_REFERENCE_INFO.](../../../extensibility/debugger/reference/debug-reference-info.md)

## <a name="syntax"></a>Sintassi

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia come parte del relativo supporto per i riferimenti agli oggetti in memoria. Questa interfaccia deve essere implementata solo se i riferimenti sono supportati.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Visual Studio chiama [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IEnumDebugReferenceInfo2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Recupera un numero specificato di [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) strutture in una sequenza di enumerazione.|
|[Saltare](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Ignora un numero specificato di [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) strutture nella sequenza di enumerazione.|
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md) (Clona)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Ottiene il numero di [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) strutture in un enumeratore.|

## <a name="remarks"></a>Osservazioni
 Un riferimento è essenzialmente un tipo e un indirizzo, mentre una proprietà è un nome, tipo e indirizzo. Un riferimento persiste finché l'oggetto a cui si fa riferimento esiste in memoria. Vedere [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) per ulteriori dettagli.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
