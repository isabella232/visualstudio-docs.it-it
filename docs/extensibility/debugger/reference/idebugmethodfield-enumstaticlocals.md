---
title: IDebugMethodField::EnumStaticLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 006f1975c18aa7464531654d9b71fd857953afc9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324248"
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
[out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco delle variabili locali statiche. Restituisce un valore null se non sono variabili locali non statiche.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK o restituisce S_FALSE se non sono variabili locali non statiche. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Ogni elemento è un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetti che rappresentano diversi tipi di variabili locali statiche. Chiamare il [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metodo su ogni oggetto per determinare esattamente quale tipo di variabile locale statica l'oggetto rappresenta.

## <a name="see-also"></a>Vedere anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)