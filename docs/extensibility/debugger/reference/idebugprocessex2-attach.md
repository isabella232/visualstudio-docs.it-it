---
title: IDebugProcessEx2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5932535810f28e6f5da96ab69457f7364563d622
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325336"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Questo metodo indica il processo a una sessione è ora il debug del processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Attach( 
   IDebugSession2* pSession
);
```

```csharp
int Attach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parametri
`pSession`\
[in] Un valore che identifica in modo univoco la sessione di connessione a questo processo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 L'interfaccia passato `pSession` deve essere considerata solo come un cookie, un valore che identifica in modo univoco la gestione del debug sessione connessione a questo processo; nessuno dei metodi nell'interfaccia specificata sono funzionali.

## <a name="see-also"></a>Vedere anche
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)