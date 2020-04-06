---
title: Proprietà IDebugEngine2::SetException . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7398db3c15c58821e05eff839a1022276401d569
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730943"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Specifica il modo in cui il motore di debug (DE) deve gestire una determinata eccezione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int SetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parametri
`pException`\
[in] Struttura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) che descrive l'eccezione e come eseguirne il debug.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Un DE potrebbe essere istruito per interrompere il programma generando un'eccezione a prima possibilità, seconda possibilità, o non a tutti.

## <a name="see-also"></a>Vedere anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
