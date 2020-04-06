---
title: Proprietà IDebugCanStopEvent2::CanStop . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2915938c966bac7f842d0745c973c7d0b7033e2b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734596"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Notifica al motore di debug (DE) se interrompere o meno nel percorso del codice corrente o semplicemente continuare l'esecuzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>Parametri
`fCanStop`\
[in] Diverso da`TRUE`zero ( ) se il DE deve arrestarsi nella posizione del codice corrente; in caso`FALSE`contrario, zero ( ).

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Il destinatario di questo evento chiama in genere il [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metodo per `IDebugCanStopEvent2::CanStop` determinare il motivo per cui il DE desidera arrestare e quindi chiama il metodo con la risposta appropriata.

 Se il DE si arresta, invia un evento che descrive il motivo dell'arresto. Esistono in genere due eventi che vengono inviati, un'interruzione del segnale o utente rappresentata dal [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interfaccia e un evento punto di interruzione rappresentato dal [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfaccia.

## <a name="see-also"></a>Vedere anche
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
