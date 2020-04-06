---
title: IDebugCanStopEvent2::GetReason ??? Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59e611c3ed69528f92a6085cf74aa44efed09144
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734531"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Ottiene il motivo per cui il motore di debug (DE) desidera arrestare.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetReason( 
   CANSTOP_REASON* pcr
);
```

```csharp
int GetReason( 
   out enum_CANSTOP_REASON pcr
);
```

## <a name="parameters"></a>Parametri
`pcr`\
[fuori] Restituisce un valore dall'enumerazione [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) che descrive il motivo di questo evento.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo viene in genere chiamato prima di [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) metodo in`TRUE`modo `IDebugCanStopEvent2::CanStop` che il chiamante può determinare se passare diverso da zero ( ) al metodo.

 Il motivo dell'arresto può essere `CANSTOP_ENTRYPOINT`, il che `CANSTOP_STEPIN`significa che il DE ha raggiunto un punto di ingresso, o , il che significa che il DE ha eseguito l'eseguito l'eseguito l'eseguito l'operazione in una funzione.

## <a name="see-also"></a>Vedere anche
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
