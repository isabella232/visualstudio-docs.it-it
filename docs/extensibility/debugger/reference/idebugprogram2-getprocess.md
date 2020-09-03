---
title: 'IDebugProgram2:: GetProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca1842e92e7e1c164a6468e6c1e94a352ef67c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722790"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Ottenere il processo in cui è in esecuzione il programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetProcess(
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess(
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Parametri
`ppProcess`\
out Restituisce l'interfaccia [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) che rappresenta il processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 A meno che un motore di debug (DE) implementi l'interfaccia [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) , l'implementazione de di questo metodo deve sempre restituire `E_NOTIMPL` perché un de non è in grado di determinare il processo in cui è in esecuzione e pertanto non è in grado di soddisfare un'implementazione di questo metodo.

 L'implementazione dell' `IDebugEngineLaunch2` interfaccia significa che il de deve sapere come creare un processo; pertanto, l'implementazione de dell'interfaccia [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) è in grado di conoscere il processo in cui è in esecuzione.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
