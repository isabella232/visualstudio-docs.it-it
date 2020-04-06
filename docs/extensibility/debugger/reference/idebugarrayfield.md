---
title: Proprietà IDebugArrayField . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dab01c1e956ced7e6894b951ab16f4ce68eb778b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736299"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
Questa interfaccia descrive un tipo o un simbolo di matrice.

## <a name="syntax"></a>Sintassi

```
IDebugArrayField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa il [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaccia. Questa interfaccia è una specializzazione che rappresenta gli oggetti matrice.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Utilizzare [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia dal [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) `FIELD_TYPE_ARRAY`interfaccia se [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) restituisce il flag .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi sulle interfacce [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , questa interfaccia implementa quanto segue:

|Metodo|Descrizione|
|------------|-----------------|
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Ottiene il numero di elementi nella matrice.|
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Ottiene il tipo di elemento nella matrice.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Ottiene il rango della matrice.|

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
