---
description: Ottiene il motivo per cui il motore di debug (DE) desidera arrestare.
title: 'IDebugCanStopEvent2:: GetReason | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2125bb90693d5a4c5cc23ac1225d56dea636de2e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085052"
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
out Restituisce un valore dall'enumerazione [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) che descrive il motivo di questo evento.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene in genere chiamato prima del metodo [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) in modo che il chiamante possa determinare se passare un valore diverso da zero ( `TRUE` ) al `IDebugCanStopEvent2::CanStop` metodo.

 Il motivo dell'arresto può essere `CANSTOP_ENTRYPOINT` , che indica che il de ha raggiunto un punto di ingresso o `CANSTOP_STEPIN` , il che significa che l'istruzione de è stata rientrata in una funzione.

## <a name="see-also"></a>Vedi anche
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
