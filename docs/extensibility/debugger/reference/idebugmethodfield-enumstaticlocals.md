---
description: Crea un enumeratore per le variabili locali statiche del metodo.
title: 'IDebugMethodField:: EnumStaticLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c31d8644bf918b57c1d97b2ee2ddbc840a33ff1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164981"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Crea un enumeratore per le variabili locali statiche del metodo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumStaticLocals( 
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumStaticLocals(
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parametri
`ppLocals`\
out Restituisce un oggetto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco di variabili locali statiche. Restituisce un valore null se non sono presenti variabili locali statiche.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti variabili locali statiche. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Ogni elemento è un oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta tipi diversi di variabili locali statiche. Chiamare il metodo [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) su ogni oggetto per determinare esattamente il tipo di locale statico rappresentato dall'oggetto.

## <a name="see-also"></a>Vedi anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
