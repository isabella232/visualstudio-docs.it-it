---
description: Imposta il valore di riferimento di questo oggetto .
title: Interfaccia IDebugObject::SetReferenceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b18af9741c4108b2638be0d55cec78d9a4fc683f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034890"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Imposta il valore di riferimento di questo oggetto .

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
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo rende questo [oggetto IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) un riferimento al valore dell'oggetto specificato nel parametro `pObject` , generando qualsiasi riferimento precedente. Si noti che `IDebugObject` questo oggetto deve essere già un tipo riferimento.

## <a name="see-also"></a>Vedi anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [Getvalue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
