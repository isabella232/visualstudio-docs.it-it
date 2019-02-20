---
title: IDebugClassField::GetEnclosingClass | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ab5be03fc6421f03742878f2b72f568ec0915dc
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412916"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Ottiene la classe che comprende questa classe.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

#### <a name="parameters"></a>Parametri
`ppClassField`  
[out] Restituisce un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) classe oggetto che rappresenta il tipo di inclusione. Restituisce un valore null se nessuna classe che lo contiene.

## <a name="return-value"></a>Valore restituito
Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
Se la classe rappresentata da questo [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto è una classe annidata, il `ppClassField` parametro restituisce un `IDebugClassField` classe oggetto che rappresenta il tipo di inclusione. Ad esempio, Data questa definizione di classe:

```
class RootClass {
    class NestedClass { }
};
```

Chiama il `GetEnclosingClass` metodo sul `IDebugClassField` oggetto che rappresenta il `NestedClass` classe restituisce un' `IDebugClassField` oggetto che rappresenta la classe `RootClass`.

## <a name="see-also"></a>Vedere anche
[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
