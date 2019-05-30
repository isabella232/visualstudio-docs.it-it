---
title: IDebugMethodField::EnumArguments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f0c5f95267948b6fb2c1cab1a7d79a2e62b9e3c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346790"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Crea un enumeratore per il tipo di ciascun argomento è necessario chiamare il metodo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parametri
`ppParams`\
[out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco dei tipi di argomento. Restituisce un valore null se non sono presenti argomenti.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_FALSE se non sono presenti argomenti restituisce S_OK. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Ogni elemento è un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetti che rappresentano i tipi di ogni parametro. Chiamare il [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metodo per recuperare le informazioni sul tipo di ogni parametro.

 Se è necessario il nome del parametro insieme al tipo, quindi chiamare il [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)