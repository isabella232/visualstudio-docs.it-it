---
title: IDebugBinder::GetFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b69af018a1b5b1ddf743784f4736d7c2ac24d45f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712294"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Questo metodo ottiene un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) oggetto utilizzato per creare parametri di funzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetFunctionObject( 
   IDebugFunctionObject **ppFunction
);
```

```csharp
int GetFunctionObject(
   out IDebugFunctionObject ppFunction
);
```

#### <a name="parameters"></a>Parametri
 `ppFunction`

 [out] Restituisce il [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia che consente di creare i parametri di funzione.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)