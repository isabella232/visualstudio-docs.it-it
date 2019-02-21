---
title: IDebugMethodField::EnumLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba6cd5e65c54355ec21d22d101d94270b95018e8
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450412"
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

#### <a name="parameters"></a>Parametri
`pAddress`  
[in] Un' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) oggetto che rappresenta l'indirizzo di debug che consente di selezionare il contesto o l'ambito da cui ottenere le variabili locali.

`ppLocals`  
[out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) dell'oggetto che rappresenta un elenco di variabili locali; in caso contrario, restituisce un valore null se non sono variabili non locali.

## <a name="return-value"></a>Valore restituito
Se l'operazione riesce, restituisce S_OK o restituisce S_FALSE se non sono variabili non locali. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
Vengono enumerate solo le variabili definite all'interno del blocco che contiene l'indirizzo di debug specificato. Se sono necessarie tutte le variabili locali incluse eventuali variabili locali generate dal compilatore, chiamare il [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) (metodo).

Un metodo può contenere più blocchi o i contesti di definizione dell'ambito. Ad esempio, il seguente metodo artificioso contiene tre ambiti, i due blocchi interni e il corpo del metodo stesso.

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

Il [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) oggetto di `func` metodo di stesso. Chiama il `EnumLocals` metodo con un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) impostato sulla `Inner Scope 1` indirizzo restituisce un'enumerazione contenente il `temp1` variabile, ad esempio.

## <a name="see-also"></a>Vedere anche
[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)  
[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)  
[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)  
[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
