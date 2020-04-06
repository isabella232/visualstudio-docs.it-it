---
title: IDebugCoreServer3::GetServerFriendlyName . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eec30783041a1240d8f85815c06f4ca60729a484
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732893"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Recupera un nome descrittivo per il server.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetServerFriendlyName(
   BSTR* pbstrName
);
```

```csharp
int GetServerFriendlyName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parametri
`pbstrName`\
[fuori] Restituisce un nome descrittivo per il server.

> [!NOTE]
> Il chiamante è responsabile della liberazione della stringa.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Osservazioni
 Per i server avviati dall'utente, il nome restituito da questo metodo è il nome completo del server. Per i server avviati automaticamente, il nome è quello del computer su cui è in esecuzione il server.

 Per un nome orientato al computer, chiamare il [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [NomeServer GetServer](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
