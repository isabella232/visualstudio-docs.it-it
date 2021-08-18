---
description: Ottiene il processo in cui è in esecuzione il programma.
title: IDebugProgram2::GetProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 135d8e632b4cef71050db0ba326388170037e732
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126544"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Ottiene il processo in cui è in esecuzione il programma.

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
[out] Restituisce [l'interfaccia IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) che rappresenta il processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 A meno che un motore di debug non implementi l'interfaccia [IDebugEngineLaunch2,](../../../extensibility/debugger/reference/idebugenginelaunch2.md) l'implementazione de di questo metodo deve sempre restituire perché de non è in grado di determinare in quale processo è in esecuzione e pertanto non può soddisfare un'implementazione di questo `E_NOTIMPL` metodo.

 L'implementazione dell'interfaccia significa che DE deve sapere come creare un `IDebugEngineLaunch2` processo. Pertanto, l'implementazione de [dell'interfaccia IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) è in grado di conoscere il processo in cui è in esecuzione.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
