---
description: Crea un enumeratore per le proprietà associate al stack frame, ad esempio le variabili locali.
title: IDebugStackFrame2::EnumProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a59cd03281fb5e802a1c93cba65115bbb9b09ee5f57c5c15d01b100b90cbf78d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121292117"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Crea un enumeratore per le proprietà associate al stack frame, ad esempio le variabili locali.

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
[in] Combinazione di flag dell DEBUGPROP_INFO_FLAGS enumere che specifica [](../../../extensibility/debugger/reference/debug-property-info.md) i campi nelle strutture DEBUG_PROPERTY_INFO valori enumerati. [](../../../extensibility/debugger/reference/debugprop-info-flags.md)

`nRadix`\
[in] Radice da utilizzare nella formattazione di qualsiasi informazione numerica.

`refiid`\
[in] GUID di un filtro utilizzato per selezionare [le](../../../extensibility/debugger/reference/debug-property-info.md) DEBUG_PROPERTY_INFO da enumerare, ad esempio `guidFilterLocals` .

`dwTimeout`\
[in] Tempo massimo, in millisecondi, di attesa prima della restituzione da questo metodo. Usare `INFINITE` per attendere a tempo indeterminato.

`pcelt`\
[out] Restituisce il numero di proprietà enumerate. Questo è lo stesso della chiamata [al metodo GetCount.](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)

`ppEnum`\
[out] Restituisce un [oggetto IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenente un elenco delle proprietà desiderate.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Poiché questo metodo consente di recuperare tutte le proprietà selezionate con una singola chiamata, è più veloce rispetto alla chiamata sequenziale dei metodi [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) [ed EnumChildren.](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)

## <a name="see-also"></a>Vedi anche
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)
- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
