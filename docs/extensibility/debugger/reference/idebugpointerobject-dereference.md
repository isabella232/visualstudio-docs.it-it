---
description: Ottiene l'oggetto a cui punta.
title: IDebugPointerObject::D ereference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 226e8471d83208e9647578fca0fa16cc7b49e4eb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087639"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Ottiene l'oggetto a cui punta.

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
in Offset di byte semplice dall'inizio dell'oggetto a cui punta.

`ppObject`\
out Restituisce un oggetto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta l'oggetto a cui punta, più l'offset, se presente.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore. Restituisce E_FAIL se l'oggetto non punta a un altro oggetto.

## <a name="remarks"></a>Commenti
 L'oggetto a cui punta può essere un tipo primitivo o più complesso, ad esempio una classe o una struttura.

## <a name="see-also"></a>Vedi anche
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
