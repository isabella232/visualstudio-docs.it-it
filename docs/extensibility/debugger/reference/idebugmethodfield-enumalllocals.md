---
description: Crea un enumeratore per tutte le variabili locali del metodo, incluse quelle generate internamente da un compilatore.
title: IDebugMethodField::EnumAllLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 199ae11fc5d0b7fc3e0fd307de5328308552fadb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043375"
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
[out] Restituisce un [oggetto IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco di tutte le variabili locali nell'ambito specificato. In caso contrario, restituisce un valore Null che indica che non sono presenti variabili locali.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti variabili locali. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Vengono enumerate solo le variabili definite all'interno del blocco che contiene l'indirizzo di debug specificato. Questo metodo include tutte le variabili locali generate dal compilatore. Se sono necessarie solo le variabili locali definite in modo esplicito nell'origine, chiamare il [metodo EnumLocals.](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)

 Un metodo può contenere più contesti o blocchi di ambito.

## <a name="see-also"></a>Vedi anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
