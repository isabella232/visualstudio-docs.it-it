---
title: IDebugProgram2::GetProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b307fb7b4a25fc5a84b30eefd65e72b4f387a07d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313771"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Ottenere il processo che questo programma è in esecuzione.

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
[out] Restituisce il [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfaccia che rappresenta il processo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 A meno che un motore di debug (DE) implementa il [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) interfaccia, l'implementazione del DE di questo metodo deve sempre restituire `E_NOTIMPL` perché un CRI non può determinare quale processo è in esecuzione in modo semplice e pertanto non è possibile soddisfare un'implementazione di questo metodo.

 Implementa il `IDebugEngineLaunch2` interfaccia significa che la Germania necessario sapere come creare un processo; pertanto, implementazione del DE del [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia è in grado di individuare i processi di cui è in esecuzione in.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)