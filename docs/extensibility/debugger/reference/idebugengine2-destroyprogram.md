---
description: Informa un motore di debug (DE) che il programma specificato è stato interrotto in modo atipico e che il DE dovrebbe pulire tutti i riferimenti al programma e inviare un evento di eliminazione del programma.
title: IDebugEngine2::D estroyProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c0a58dd5893c3235ded9c7eeb5f5d47e3ddcb380
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093847"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Informa un motore di debug (DE) che il programma specificato è stato interrotto in modo atipico e che il DE dovrebbe pulire tutti i riferimenti al programma e inviare un evento di eliminazione del programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DestroyProgram( 
   IDebugProgram2* pProgram
);
```

```cpp
int DestroyProgram( 
   IDebugProgram2 pProgram
);
```

## <a name="parameters"></a>Parametri
`pProgram`\
in Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma che è stato interrotto in modo atipico.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Dopo la chiamata a questo metodo, il DE invia successivamente un evento [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) al gestore di debug della sessione (SDM).

 Questo metodo non è implementato (restituisce `E_NOTIMPL` ) se il de viene eseguito nello stesso processo del programma di cui è in corso il debug. Questo metodo viene implementato solo se il DE viene eseguito nello stesso processo del SDM.

## <a name="see-also"></a>Vedi anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
