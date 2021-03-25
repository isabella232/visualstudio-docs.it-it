---
description: Crea un enumeratore per le variabili locali selezionate del metodo.
title: 'IDebugMethodField:: EnumLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b7ecaeac949cf139f6b18f30a10a0030002c7f0f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076680"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Crea un enumeratore per le variabili locali selezionate del metodo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumLocals(
    IDebugAddress*     pAddress,
    IEnumDebugFields** ppLocals
);
```

```csharp
int EnumLocals(
    IDebugAddress        pAddress,
    out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parametri
`pAddress`\
in Oggetto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) che rappresenta l'indirizzo di debug che seleziona il contesto o l'ambito da cui ottenere le variabili locali.

`ppLocals`\
out Restituisce un oggetto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta un elenco di variabili locali. in caso contrario, restituisce un valore null se non sono presenti variabili locali.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti variabili locali. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
Vengono enumerate solo le variabili definite all'interno del blocco che contiene l'indirizzo di debug specificato. Se sono necessarie tutte le variabili locali, incluse quelle generate dal compilatore, chiamare il metodo [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) .

Un metodo può contenere più contesti di ambito o blocchi. Il metodo escogitato seguente, ad esempio, contiene tre ambiti, i due blocchi interni e il corpo del metodo stesso.

```csharp
public void func(int index)
{
    // Method body scope
    int a = 0;
    if (index == 1)
    {
        // Inner scope 1
        int temp1 = a;
    }
    else
    {
        // Inner scope 2
        int temp2 = a;
    }
}
```

L'oggetto [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) rappresenta il `func` metodo stesso. Se si chiama il `EnumLocals` metodo con un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) impostato sull' `Inner Scope 1` Indirizzo, viene restituita un'enumerazione che contiene la `temp1` variabile, ad esempio.

## <a name="see-also"></a>Vedi anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
