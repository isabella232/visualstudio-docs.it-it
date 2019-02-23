---
title: IDebugDefaultPort2::GetServer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cbfc81495c1f2319117a236246f1e7c47f3e582
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678646"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Questo metodo ottiene un'interfaccia per il server su questa porta.

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

#### <a name="parameters"></a>Parametri
 `ppServer`

 [out] Restituisce un oggetto che implementa il [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) interfaccia.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Il [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) viene implementata da Visual Studio e rappresenta il server che la porta si trova in.

## <a name="see-also"></a>Vedere anche
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)