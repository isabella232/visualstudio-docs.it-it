---
description: Crea un enumeratore per le variabili locali statiche del metodo.
title: IDebugMethodField::EnumStaticLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 05a1b7e5b0d00320bf74b04bf7f82534cdba7b5124d1e0241cb028995bd92609
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417054"
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
[out] Restituisce un [oggetto IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco di variabili locali statiche. Restituisce un valore Null se non sono presenti variabili locali statiche.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti variabili locali statiche. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Ogni elemento è un [oggetto IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta tipi diversi di variabili locali statiche. Chiamare il [metodo GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) su ogni oggetto per determinare esattamente il tipo di locale statico rappresentato dall'oggetto.

## <a name="see-also"></a>Vedi anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
