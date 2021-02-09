---
title: 'IDebugClassField:: GetEnclosingClass | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91a4e04e26a57247a541c565ea4f0f392a413d39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925046"
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
out Restituisce un oggetto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) che rappresenta la classe contenitore. Restituisce un valore null se non è presente alcuna classe contenitore.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
Se la classe rappresentata da questo oggetto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) è una classe annidata, il `ppClassField` parametro restituisce un `IDebugClassField` oggetto che rappresenta la classe contenitore. Ad esempio, data questa definizione di classe:

```
class RootClass {
    class NestedClass { }
};
```

La chiamata al `GetEnclosingClass` metodo sull' `IDebugClassField` oggetto che rappresenta la `NestedClass` classe restituisce un `IDebugClassField` oggetto che rappresenta la classe `RootClass` .

## <a name="see-also"></a>Vedi anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
