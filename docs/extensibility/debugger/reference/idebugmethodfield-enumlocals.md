---
description: Crea un enumeratore per le variabili locali selezionate del metodo .
title: IDebugMethodField::EnumLocals | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2b9ea26c91f441ee5615e86bade7e1e412d59837e28d7fe3eedab06e715540c7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121339576"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Crea un enumeratore per le variabili locali selezionate del metodo .

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
[in] Oggetto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) che rappresenta l'indirizzo di debug che seleziona il contesto o l'ambito da cui ottenere le variabili locali.

`ppLocals`\
[out] Restituisce un [oggetto IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta un elenco di variabili locali. In caso contrario, restituisce un valore Null se non sono presenti variabili locali.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti variabili locali. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
Vengono enumerate solo le variabili definite all'interno del blocco che contiene l'indirizzo di debug specificato. Se sono necessarie tutte le variabili locali, incluse le variabili locali generate dal compilatore, chiamare il [metodo EnumAllLocals.](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)

Un metodo può contenere più contesti o blocchi di ambito. Ad esempio, il metodo contrived seguente contiene tre ambiti, i due blocchi interni e il corpo del metodo stesso.

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

[L'oggetto IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) rappresenta il `func` metodo stesso. La chiamata `EnumLocals` del metodo con un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) impostato sull'indirizzo restituisce un'enumerazione `Inner Scope 1` contenente la variabile , ad esempio `temp1` .

## <a name="see-also"></a>Vedi anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
