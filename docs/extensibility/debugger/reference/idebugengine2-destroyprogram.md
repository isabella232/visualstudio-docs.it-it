---
title: IDebugEngine2::DestroyProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f626005621604d367f5878e36899aa2ff46114ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875232"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Informa un motore di debug (DE) che il programma specificato è stato terminato insolitamente e che la Germania Pulisce tutti i riferimenti al programma e un programma invia un evento di eliminazione.

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

#### <a name="parameters"></a>Parametri
 `pProgram`

 [in] Un' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta il programma di cui è stato terminato insolitamente.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Dopo che questo metodo viene chiamato, la Germania invia successivamente una [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) evento al gestore di sessione di debug (SDM).

 Questo metodo non è implementato (restituisce `E_NOTIMPL`) se la Germania è in esecuzione nello stesso processo del programma in fase di debug. Questo metodo viene implementato solo se la Germania viene eseguito nello stesso processo come il modello SDM.

## <a name="see-also"></a>Vedere anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)