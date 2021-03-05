---
description: Imposta il valore di riferimento di questo oggetto.
title: 'IDebugObject:: SetReferenceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb376e4399157f9f9fe393086cca8fcf94c3b9de
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161424"
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
in Oggetto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta il nuovo valore di riferimento.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo fa in modo che questo oggetto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) un riferimento al valore dell'oggetto specificato nel `pObject` parametro, eliminando eventuali riferimenti precedenti. Si noti che questo `IDebugObject` oggetto deve essere già un tipo riferimento.

## <a name="see-also"></a>Vedi anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
