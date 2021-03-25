---
description: Crea un enumeratore per il tipo di ogni argomento necessario per chiamare il metodo.
title: 'IDebugMethodField:: EnumArguments | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3ba48eb4d98c1ab331ee898a219584b7a4b6cf1c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058417"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Crea un enumeratore per il tipo di ogni argomento necessario per chiamare il metodo.

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
out Restituisce un oggetto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco di tipi di argomento. Restituisce un valore null se non sono presenti argomenti.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti argomenti. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Ogni elemento è un oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta i tipi di ogni parametro. Chiamare il metodo [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) per recuperare informazioni sul tipo di ogni parametro.

 Se il nome del parametro è necessario insieme al tipo, chiamare il metodo [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
