---
title: 'IDebugBinder3:: FindAlias | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a697e39d21b1c25a98c09ad6cc4837cca7a293
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735869"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Questo metodo individua un alias, dato un nome. Questa operazione eseguirà la ricerca in tutti gli alias del programma.

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
in Nome dell'alias da trovare.

`ppAlias`\
out Alias trovato, se presente, rappresentato dall'interfaccia [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` (se alias non viene trovato) o un codice di errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo inizializza l'oggetto di destinazione su null prima di chiamare. quindi verifica un valore null in seguito per determinare se l'alias è stato trovato o meno.

## <a name="see-also"></a>Vedere anche
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
