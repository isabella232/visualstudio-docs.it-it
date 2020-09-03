---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3dbe6d813b85865b0fdbc20296473684203a3f1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732375"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Questo metodo ottiene un'interfaccia per il server su cui si trova la porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetServer(
   IDebugCoreServer3** ppServer
);
```

```csharp
int GetServer(
   out IDebugCoreServer3 ppServer
);
```

## <a name="parameters"></a>Parametri
`ppServer`\
out Restituisce un oggetto che implementa l'interfaccia [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) viene implementato da Visual Studio e rappresenta il server in cui si trova la porta.

## <a name="see-also"></a>Vedere anche
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
