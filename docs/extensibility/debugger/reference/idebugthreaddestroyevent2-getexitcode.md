---
description: Ottiene il codice di uscita per un thread.
title: 'IDebugThreadDestroyEvent2:: GetExitCode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThreadDestroyEvent2::GetExitCode
helpviewer_keywords:
- IDebugThreadDestroyEvent2::GetExitCode
ms.assetid: 8bf47a17-f811-4d9b-bcea-7488908830ff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b569d526ace8b178d3758e62e36895f5ec0262c5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086833"
---
# <a name="idebugthreaddestroyevent2getexitcode"></a>IDebugThreadDestroyEvent2::GetExitCode
Ottiene il codice di uscita per un thread.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetExitCode ( 
   DWORD* pdwExit
);
```

```csharp
int GetExitCode ( 
   out uint pdwExit
);
```

## <a name="parameters"></a>Parametri
`pdwExit`\
out Restituisce il codice di uscita del thread.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)
