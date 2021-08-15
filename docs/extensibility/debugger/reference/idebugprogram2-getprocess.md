---
description: Ottenere il processo in cui è in esecuzione il programma.
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
ms.openlocfilehash: d0f7551b86bd6eb818b1e451d2cc65426cf7441d85da0812afe215dcfaa2feca
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307115"
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
[out] Restituisce [l'interfaccia IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) che rappresenta il processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 A meno che un motore di debug (DE) non implementi [l'interfaccia IDebugEngineLaunch2,](../../../extensibility/debugger/reference/idebugenginelaunch2.md) l'implementazione del metodo deve sempre restituire perché un DE non è in grado di determinare il processo in esecuzione in e pertanto non può soddisfare un'implementazione di `E_NOTIMPL` questo metodo.

 L'implementazione dell'interfaccia significa che il derea deve sapere come creare un processo. Di `IDebugEngineLaunch2` conseguenza, l'implementazione del de dell'interfaccia [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) è in grado di sapere in quale processo è in esecuzione.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
