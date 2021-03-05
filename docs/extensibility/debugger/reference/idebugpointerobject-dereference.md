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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4aa96f726ec18e84aceba159fe9be6128456ce0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169691"
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
