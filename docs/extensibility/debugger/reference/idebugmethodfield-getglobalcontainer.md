---
title: IDebugMethodField::GetGlobalContainer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77f3d82beab43b227dd3beb772dd41353d89b6fe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324181"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Ottiene il contenitore globale del metodo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parametri
`ppClass`\
[out] Restituisce un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) che rappresenta il modulo in cui questo metodo è definito.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 L'oggetto restituito [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto rappresenta l'intero modulo ed è un oggetto fittizio, vale a dire, il modulo stesso non dispone di una classe effettiva ma può essere rappresentato da un `IDebugClassField` oggetto, che consente i vari elementi del modulo per essere enumerati e individuati.

## <a name="see-also"></a>Vedere anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)