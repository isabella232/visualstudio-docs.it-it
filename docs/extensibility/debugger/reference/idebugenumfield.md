---
title: IDebugEnumField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e2bcb8f8562b5b20231879d46c64eb73af027f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920249"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Questa interfaccia rappresenta un tipo di enumerazione.

## <a name="syntax"></a>Sintassi

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia per rappresentare un'enumerazione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Uso [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia dalle [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia se [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) restituisce `FIELD_TYPE_ENUM`.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine VTable
 Oltre ai metodi nel `IDebugField` e `IDebugContainerField` interfacce, questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Restituisce un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descrive il nome per questo tipo di enumerazione.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Restituisce il nome della costante di enumerazione associata al valore specificato.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Restituisce il valore associato al nome di costante di enumerazione specificato|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Restituisce il valore associato con il nome di costante di enumerazione specificato, ma ignorando i casi.|

## <a name="remarks"></a>Note
 È il simbolo sottostante che è effettivamente associato a un percorso con [associare](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)