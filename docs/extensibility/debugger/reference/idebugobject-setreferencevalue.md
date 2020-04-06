---
title: Proprietà IDebugObject::SetReferenceValue . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc0db8ee7f0581a4c336111d3876c24f0e5c12d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726373"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Imposta il valore di riferimento di questo oggetto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>Parametri
`pObject`\
[in] Oggetto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta il nuovo valore di riferimento.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo rende questo [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto un riferimento al `pObject` valore dell'oggetto specificato nel parametro, gettando via qualsiasi riferimento precedente. Si noti che questo `IDebugObject` oggetto deve essere già un tipo di riferimento.

## <a name="see-also"></a>Vedere anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
