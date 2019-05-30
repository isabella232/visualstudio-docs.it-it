---
title: IDebugProgram2::CauseBreak | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a01b5982b4f747bd70c3a35bc0b7191bb54cd21b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311353"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Le richieste che il programma di arresta l'esecuzione successiva ora di uno dei tentativi thread di esecuzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Un' [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) evento viene inviato quando il programma quindi tenta di eseguire codice dopo questo metodo viene chiamato.

 Questo metodo è asincrono, in quanto il metodo viene restituito immediatamente senza dover necessariamente attendere il blocco del programma.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)