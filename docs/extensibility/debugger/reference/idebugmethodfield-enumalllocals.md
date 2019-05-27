---
title: IDebugMethodField::EnumAllLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92467655a8f3baaf347a28a30fbeb40fc0b3731c
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210342"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Crea un enumeratore per tutte le variabili locali del metodo, inclusi quelli generati internamente da un compilatore.

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
[in] Un' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) oggetto che rappresenta un indirizzo di debug all'interno del metodo, che punta a un ambito specifico o di contesto.

`ppLocals`\
[out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) rappresentano l'elenco di tutte le variabili locali nell'ambito specificato dell'oggetto; in caso contrario, restituisce un valore null indicante che nessuna variabile locale.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK o restituisce S_FALSE se non sono variabili non locali. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Vengono enumerate solo le variabili definite all'interno del blocco che contiene l'indirizzo di debug specificato. Questo metodo include le variabili locali generate dal compilatore. Se tutto ciò che serve sono variabili locali definite in modo esplicito nell'origine, chiamata di [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) (metodo).

 Un metodo può contenere più blocchi o i contesti di definizione dell'ambito.

## <a name="see-also"></a>Vedere anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)