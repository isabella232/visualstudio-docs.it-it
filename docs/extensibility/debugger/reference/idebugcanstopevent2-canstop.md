---
description: Notifica al motore di debug se arrestarsi o meno nel percorso del codice corrente o semplicemente continuare l'esecuzione.
title: IDebugCanStopEvent2::CanStop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd575d6bb1afdf296eff6ec3ac3a08a9551618b8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636371"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Notifica al motore di debug se arrestarsi o meno nel percorso del codice corrente o semplicemente continuare l'esecuzione.

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
[in] Diverso da zero ( `TRUE` ) se de deve arrestarsi nella posizione del codice corrente; in caso contrario, zero ( `FALSE` ).

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il ricevitore di questo evento chiama in genere il [metodo GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) per determinare il motivo per cui la deresod vuole arrestare e quindi chiama il metodo `IDebugCanStopEvent2::CanStop` con la risposta appropriata.

 Se il de viene arrestato, invia un evento che descrive il motivo dell'arresto. In genere vengono inviati due eventi, un'interruzione di segnale o utente rappresentata dall'interfaccia [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) e un evento punto di interruzione rappresentato [dall'interfaccia IDebugBreakpointEvent2.](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)

## <a name="see-also"></a>Vedi anche
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
