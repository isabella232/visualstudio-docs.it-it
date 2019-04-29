---
title: IDebugObject::SetReferenceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5cf00fc85a2b3f3dc09704227f84fa5b2e90ee6f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918479"
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

#### <a name="parameters"></a>Parametri
 `pObject`

 [in] Un' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto che rappresenta il nuovo valore di riferimento.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo rende questa [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) sul valore dell'oggetto specificato in un riferimento a un oggetto di `pObject` parametro, generando un'eccezione qualsiasi riferimento precedente. Si noti che questo `IDebugObject` oggetto deve essere già un tipo di riferimento.

## <a name="see-also"></a>Vedere anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)