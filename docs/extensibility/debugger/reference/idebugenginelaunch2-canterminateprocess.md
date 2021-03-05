---
description: Determina se un processo può essere terminato.
title: 'IDebugEngineLaunch2:: CanTerminateProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 687b2816c6fd312efef29daa44e0644fc5c5c8c6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153625"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
Determina se un processo può essere terminato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanTerminateProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int CanTerminateProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>Parametri
`pProcess`\
in Oggetto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) che rappresenta il processo da terminare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore. Restituisce `S_FALSE` se il motore non è in grado di terminare il processo, ad esempio perché l'accesso è stato negato.

## <a name="remarks"></a>Commenti
 Se questo metodo restituisce `S_OK` , è possibile chiamare il metodo [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) per terminare effettivamente il processo.

## <a name="see-also"></a>Vedi anche
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)
