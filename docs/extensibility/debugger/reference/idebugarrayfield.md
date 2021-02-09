---
title: IDebugArrayField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 64717948f6406d1c6e9a5c1fabfec4b3a16bf116
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870259"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
Questa interfaccia descrive un simbolo o un tipo di matrice.

## <a name="syntax"></a>Sintassi

```
IDebugArrayField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa l'interfaccia [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) . Questa interfaccia è una specializzazione che rappresenta oggetti matrice.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Usare [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia dall'interfaccia [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) se [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) restituisce il flag `FIELD_TYPE_ARRAY` .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi nelle interfacce [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , questa interfaccia implementa gli elementi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Ottiene il numero di elementi nella matrice.|
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Ottiene il tipo di elemento nella matrice.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Ottiene l'ordine di priorità della matrice.|

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
