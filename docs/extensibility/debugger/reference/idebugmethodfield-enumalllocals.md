---
title: IDebugMethodField::EnumAllLocals ??? Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50da5af616c56276a0299a0d08e6eeb0b88181cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727336"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Crea un enumeratore per tutte le variabili locali del metodo, incluse quelle generate internamente da un compilatore.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parametri
`pAddress`\
[in] Oggetto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) che rappresenta un indirizzo di debug all'interno del metodo, che punta a un ambito o a un contesto specifico.

`ppLocals`\
[fuori] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco di tutte le variabili locali nell'ambito specificato; in caso contrario, restituisce un valore null che indica nessuna variabili locali.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti variabili locali. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Osservazioni
 Vengono enumerate solo le variabili definite all'interno del blocco che contiene l'indirizzo di debug specificato. Questo metodo include tutte le variabili locali generate dal compilatore. Se tutto ciò che è necessario sono le variabili locali definite in modo esplicito nell'origine, chiamare il [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) metodo.

 Un metodo può contenere più contesti di ambito o blocchi.

## <a name="see-also"></a>Vedere anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
