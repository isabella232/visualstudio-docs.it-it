---
title: Proprietà IDebugObject::SetValue . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e4652eb3c77a1871063dfa71b464fb1f7c43f94
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726361"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Imposta il valore dell'oggetto da una serie consecutiva di byte.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

## <a name="parameters"></a>Parametri
`pValue`\
[in] Matrice di byte che rappresenta il nuovo valore.

`nSize`\
[in] Dimensione del valore in byte.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 I valori nella matrice vengono copiati in questo [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto, sostituendo qualsiasi valore esistente. La dimensione del nuovo valore può essere maggiore o minore del valore esistente. Non `IDebugObject` può essere un riferimento null.

## <a name="see-also"></a>Vedere anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
