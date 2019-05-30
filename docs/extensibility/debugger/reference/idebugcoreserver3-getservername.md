---
title: IDebugCoreServer3::GetServerName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerName
helpviewer_keywords:
- IDebugCoreServer3::GetServerName
ms.assetid: 0fc3fcf5-d6a3-4a00-bf14-458b8645714e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6fe2a6425e55e3e0fdb56dc1e4cb4429dd9d4df3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327031"
---
# <a name="idebugcoreserver3getservername"></a>IDebugCoreServer3::GetServerName
Recupera il nome del server.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetServerName(
   BSTR* pbstrName
);
```

```csharp
int GetServerName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parametri
`pbstrName`\
[out] Restituisce il nome del server.

> [!NOTE]
> Il chiamante è responsabile della liberazione della stringa.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Note
 Per un nome descrittivo del server, chiamare il [GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)