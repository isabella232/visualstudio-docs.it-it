---
description: Questo metodo informa il processo che una sessione sta ora eseguendo il debug del processo.
title: 'IDebugProcessEx2:: alleghi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1938ae8299612caabe2fe684b7b5c1af685d4596
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149743"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Questo metodo informa il processo che una sessione sta ora eseguendo il debug del processo.

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
in Valore che identifica in modo univoco la sessione che si connette al processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'interfaccia passata deve `pSession` essere considerata solo come un cookie, un valore che identifica in modo univoco la gestione del debug della sessione che si connette al processo; nessuno dei metodi nell'interfaccia fornita è funzionante.

## <a name="see-also"></a>Vedi anche
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
