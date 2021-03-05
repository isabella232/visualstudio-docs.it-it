---
description: Specifica il modo in cui il motore di debug (DE) deve gestire un'eccezione specificata.
title: 'IDebugEngine2:: seexception | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 543cccbbefd12accd75213f255f8e3b677cdea38
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153937"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Specifica il modo in cui il motore di debug (DE) deve gestire un'eccezione specificata.

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
in Struttura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) che descrive l'eccezione e come eseguirne il debug.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 È possibile che venga richiesto all'utente di arrestare il programma che genera un'eccezione al primo tentativo, alla seconda possibilità o non a tutti.

## <a name="see-also"></a>Vedi anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
