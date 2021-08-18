---
description: Ottiene la classe che racchiude questa classe.
title: IDebugClassField::GetEnclosingClass | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd6f6314afd1489609d5f93a44f3645cb70de8e8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122072416"
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
[out] Restituisce un [oggetto IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) che rappresenta la classe contenitore. Restituisce un valore Null se non esiste alcuna classe contenitore.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
Se la classe rappresentata da questo [oggetto IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) è una classe annidata, il parametro restituisce un oggetto che `ppClassField` rappresenta la classe `IDebugClassField` contenitore. Ad esempio, data questa definizione di classe:

```
class RootClass {
    class NestedClass { }
};
```

La chiamata `GetEnclosingClass` al metodo `IDebugClassField` sull'oggetto che rappresenta `NestedClass` la classe restituisce un oggetto che rappresenta la classe `IDebugClassField` `RootClass` .

## <a name="see-also"></a>Vedi anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
