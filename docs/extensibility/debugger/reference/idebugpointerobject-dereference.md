---
title: IDebugPointerObject::Dereference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 381c6f392cccb398497204cc5772c5f9a00fd5b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331651"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Ottiene l'oggetto puntato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametri
`dwIndex`\
[in] Un offset di byte semplici dall'inizio dell'oggetto puntato.

`ppObject`\
[out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) dell'oggetto che rappresenta l'oggetto a cui, oltre a eseguire l'offset, se presente.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore. Restituisce E_FAIL se questo oggetto non fa riferimento a un altro oggetto.

## <a name="remarks"></a>Note
 L'oggetto a cui può essere primitivo o un tipo più complesso, ad esempio una classe o struttura.

## <a name="see-also"></a>Vedere anche
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)