---
title: IDebugEnumField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7885f36a113809e81279498a769e257af4f1cde2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730166"
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
 Usare [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia dall'interfaccia [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) se [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) restituisce `FIELD_TYPE_ENUM` .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine VTable
 Oltre ai metodi sulle `IDebugField` `IDebugContainerField` interfacce e, questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Restituisce un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descrive il nome per questo tipo di enumerazione.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Restituisce il nome della costante di enumerazione associata al valore specificato.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Restituisce il valore associato al nome della costante di enumerazione specificata.|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Restituisce il valore associato al nome della costante di enumerazione specificato ma ignorando la distinzione tra maiuscole e minuscole.|

## <a name="remarks"></a>Osservazioni
 Si tratta del simbolo sottostante che è effettivamente associato a una posizione con [Binding](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Associazione](../../../extensibility/debugger/reference/idebugbinder-bind.md)
