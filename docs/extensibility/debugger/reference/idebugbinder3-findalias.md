---
title: IDebugBinder3::FindAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8387a3302395d6e25c2b00dd360286e533531168
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344427"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Questo metodo individua un alias, dato un nome. Si eseguirà la ricerca tutti gli alias nel programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametri
`pcstrName`\
[in] Nome di alias da trovare.

`ppAlias`\
[out] Alias (se presente) rappresentato dal [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interfaccia.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` (se non viene trovato alias) o un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo inizializza l'oggetto di destinazione a null prima di chiamare il metodo. quindi verifica un valore null in un secondo momento determinare se l'alias è stato trovato.

## <a name="see-also"></a>Vedere anche
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)