---
title: 'IDebugProcess2:: GetServer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetServer
helpviewer_keywords:
- IDebugProcess2::GetServer
ms.assetid: 8f73c530-cceb-4f1f-8c63-1cc0ccd4a310
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f3e8a1553d374f7eaddaace3e3a2ad4a0c882b20
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890071"
---
# <a name="idebugprocess2getserver"></a>IDebugProcess2::GetServer
Ottiene il server in cui è in esecuzione il processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetServer( 
   IDebugCoreServer2** ppServer
);
```

```csharp
int GetServer( 
   out IDebugCoreServer2 ppServer
);
```

## <a name="parameters"></a>Parametri
`ppServer`\
out Restituisce un oggetto [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) che rappresenta il server in cui è in esecuzione il processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 È possibile eseguire più di un server in un singolo computer.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
