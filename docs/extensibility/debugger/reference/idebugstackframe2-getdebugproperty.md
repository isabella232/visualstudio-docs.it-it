---
title: 'IDebugStackFrame2:: GetDebugProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDebugProperty
helpviewer_keywords:
- IDebugStackFrame2::GetDebugProperty
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aa98107ada265d232647d27b4050b507d4581df7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719792"
---
# <a name="idebugstackframe2getdebugproperty"></a>IDebugStackFrame2::GetDebugProperty
Ottiene una descrizione delle proprietà di un stack frame.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetDebugProperty ( 
   IDebugProperty2** ppDebugProp
);
```

```csharp
int GetDebugProperty ( 
   out IDebugProperty2 ppDebugProp
);
```

## <a name="parameters"></a>Parametri
`ppDebugProp`\
out Restituisce un oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che descrive le proprietà di questo stack frame.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 La chiamata al metodo [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) con i filtri appropriati può recuperare le variabili locali, i parametri del metodo, i registri e il puntatore "This" associato all'stack frame.

## <a name="see-also"></a>Vedere anche
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
