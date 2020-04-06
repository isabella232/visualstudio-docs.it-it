---
title: Proprietà IDebugClassField::GetEnclosingClass . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5a68e32da370d6881eb2b74cbca157f7b899329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734401"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Ottiene la classe che racchiude questa classe.

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

## <a name="parameters"></a>Parametri
`ppClassField`\
[fuori] Restituisce un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto che rappresenta la classe che lo contiene. Restituisce un valore null se non è presente alcuna classe di inclusione.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
Se la classe rappresentata da questo [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) `ppClassField` oggetto è `IDebugClassField` una classe annidata, il parametro restituisce un oggetto che rappresenta la classe che lo contiene. Ad esempio, data questa definizione di classe:For example, given this class definition:

```
class RootClass {
    class NestedClass { }
};
```

La `GetEnclosingClass` chiamata del `IDebugClassField` metodo sull'oggetto che rappresenta la `NestedClass` classe restituisce un `IDebugClassField` oggetto che rappresenta la classe `RootClass`.

## <a name="see-also"></a>Vedere anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
