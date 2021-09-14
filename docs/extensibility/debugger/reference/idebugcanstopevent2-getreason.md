---
description: Ottiene il motivo per cui il motore di debug (DE) vuole arrestarsi.
title: IDebugCanStopEvent2::GetReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ef456e484347aa278e5a3c44799eecc8949a565
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627479"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Ottiene il motivo per cui il motore di debug (DE) vuole arrestarsi.

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
[out] Restituisce un valore [dall'CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) che descrive il motivo dell'evento.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene in genere chiamato prima del metodo [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) in modo che il chiamante possa determinare se passare un valore diverso da zero ( `TRUE` ) al `IDebugCanStopEvent2::CanStop` metodo.

 Il motivo dell'arresto può essere , che significa che il de ha raggiunto un punto di ingresso o , il che significa che il de è stato inserito `CANSTOP_ENTRYPOINT` `CANSTOP_STEPIN` in una funzione.

## <a name="see-also"></a>Vedi anche
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
