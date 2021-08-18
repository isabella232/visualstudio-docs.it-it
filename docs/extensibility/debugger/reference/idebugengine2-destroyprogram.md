---
description: Informa un motore di debug (DE) che il programma specificato è stato terminato atipicamente e che il de deve pulire tutti i riferimenti al programma e inviare un evento di eliminazione del programma.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 49256244f5839341c66f5a308505c18c0737eace
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119139"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Informa un motore di debug (DE) che il programma specificato è stato terminato atipicamente e che il de deve pulire tutti i riferimenti al programma e inviare un evento di eliminazione del programma.

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
[in] Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma terminato atipicamente.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Dopo la chiamata di questo metodo, il DE invia successivamente un evento [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) al gestore di debug sessione (SDM).

 Questo metodo non viene implementato (restituisce `E_NOTIMPL` ) se il de viene eseguito nello stesso processo del programma di cui viene eseguito il debug. Questo metodo viene implementato solo se de viene eseguito nello stesso processo di SDM.

## <a name="see-also"></a>Vedi anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
