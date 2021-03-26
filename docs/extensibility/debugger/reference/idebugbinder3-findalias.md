---
description: Questo metodo individua un alias, dato un nome.
title: 'IDebugBinder3:: FindAlias | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9958c1c2b93d6547f1f3453bafc9e331f9061844
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089056"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Questo metodo individua un alias, dato un nome. Questa operazione eseguirà la ricerca in tutti gli alias del programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametri
`pcstrName`\
in Nome dell'alias da trovare.

`ppAlias`\
out Alias trovato, se presente, rappresentato dall'interfaccia [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` (se alias non viene trovato) o un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo inizializza l'oggetto di destinazione su null prima di chiamare. quindi verifica un valore null in seguito per determinare se l'alias è stato trovato o meno.

## <a name="see-also"></a>Vedi anche
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
