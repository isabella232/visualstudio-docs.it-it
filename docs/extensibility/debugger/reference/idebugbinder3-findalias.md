---
description: Questo metodo individua un alias, dato un nome.
title: IDebugBinder3::FindAlias | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8138d702fb8507cfb1da24f28995b2bc4d21341f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627492"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Questo metodo individua un alias, dato un nome. In questo modo verranno cercati tutti gli alias nel programma.

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
[in] Nome dell'alias da trovare.

`ppAlias`\
[out] Alias trovato (se presente) rappresentato [dall'interfaccia IDebugAlias.](../../../extensibility/debugger/reference/idebugalias.md)

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, `S_OK` restituisce ; in caso contrario, restituisce `S_FALSE` (se l'alias non viene trovato) o un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo inizializza l'oggetto di destinazione su Null prima di chiamare . verifica quindi la corrispondenza di un valore Null in un secondo momento per determinare se l'alias è stato trovato o meno.

## <a name="see-also"></a>Vedi anche
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
