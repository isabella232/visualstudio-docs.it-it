---
title: IDebugMethodField::EnumArguments Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: adbb1ea4c9172a5f1cee877d04b81aed938bf7a5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727254"
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
[fuori] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco di tipi di argomento. Restituisce un valore null se non sono presenti argomenti.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti argomenti. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Osservazioni
 Ogni elemento è un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto che rappresenta i tipi di ogni parametro. Chiamare il [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metodo per recuperare informazioni sul tipo di ogni parametro.

 Se il nome del parametro è necessario insieme al tipo, quindi chiamare il [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
