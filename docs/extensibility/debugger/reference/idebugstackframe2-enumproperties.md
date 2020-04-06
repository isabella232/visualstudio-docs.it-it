---
title: Proprietà IDebugStackFrame2::EnumProperties . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f822f20cf4fb7a6fd5aa71b9cc1ec26bcd90e234
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719903"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Crea un enumeratore per le proprietà associate allo stack frame, ad esempio le variabili locali.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumProperties ( 
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,
   UINT                      nRadix,
   REFIID                    refiid,
   DWORD                     dwTimeout,
   ULONG*                    pcelt,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumProperties ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,
   uint                        nRadix,
   ref Guid                    refiid,
   uint                        dwTimeout,
   out uint                    pcelt,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametri
`dwFieldSpec`\
[in] Combinazione di flag dell'enumerazione [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) che specifica quali campi nelle strutture [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) enumerate devono essere compilate.

`nRadix`\
[in] La radice da utilizzare nella formattazione di qualsiasi informazione numerica.

`refiid`\
[in] GUID di un filtro utilizzato per selezionare le [strutture](../../../extensibility/debugger/reference/debug-property-info.md) `guidFilterLocals`DEBUG_PROPERTY_INFO devono essere enumerate, ad esempio .

`dwTimeout`\
[in] Tempo massimo, in millisecondi, di attesa prima della restituzione da questo metodo. Utilizzare `INFINITE` per attendere a tempo indeterminato.

`pcelt`\
[fuori] Restituisce il numero di proprietà enumerate. Equivale a chiamare il metodo [GetCount.This](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) is the same as calling the GetCount method.

`ppEnum`\
[fuori] Restituisce un [oggetto IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenente un elenco delle proprietà desiderate.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Poiché questo metodo consente di recuperare tutte le proprietà selezionate con una singola chiamata, è più veloce rispetto alla chiamata sequenziale di [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) e [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metodi.

## <a name="see-also"></a>Vedere anche
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)
- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
