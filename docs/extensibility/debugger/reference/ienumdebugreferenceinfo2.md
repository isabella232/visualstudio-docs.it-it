---
description: Questa interfaccia enumera DEBUG_REFERENCE_INFO strutture .
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e9b89ee48a0975a8b2e9c438267c17b5e94bd26b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636292"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Questa interfaccia enumera [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) strutture .

## <a name="syntax"></a>Sintassi

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia come parte del supporto per i riferimenti a oggetti in memoria. Questa interfaccia deve essere implementata solo se i riferimenti sono supportati.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Visual Studio chiama [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IEnumDebugReferenceInfo2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Recupera un numero specificato di strutture [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Ignora un numero specificato di [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) nella sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Ottiene il numero di [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) in un enumeratore.|

## <a name="remarks"></a>Commenti
 Un riferimento è essenzialmente un tipo e un indirizzo, mentre una proprietà è un nome, un tipo e un indirizzo. Un riferimento viene mantenuto finché l'oggetto a cui si fa riferimento è presente in memoria. Per [altri dettagli, vedere IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
