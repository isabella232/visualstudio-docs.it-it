---
description: Questo metodo ottiene un'interfaccia per il server su cui si trova la porta.
title: 'IDebugDefaultPort2:: GetServer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d5bfd242cd3f441bf094f94e41a78e240f1ec46
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162979"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Questo metodo ottiene un'interfaccia per il server su cui si trova la porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetServer(
   IDebugCoreServer3** ppServer
);
```

```csharp
int GetServer(
   out IDebugCoreServer3 ppServer
);
```

## <a name="parameters"></a>Parametri
`ppServer`\
out Restituisce un oggetto che implementa l'interfaccia [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) viene implementato da Visual Studio e rappresenta il server in cui si trova la porta.

## <a name="see-also"></a>Vedi anche
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
