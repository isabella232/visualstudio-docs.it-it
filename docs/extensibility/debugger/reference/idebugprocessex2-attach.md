---
description: Questo metodo informa il processo che una sessione sta ora debug del processo.
title: IDebugProcessEx2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5687031d1b4cd0be439ef1953f54a609e19f6366
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071926"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Questo metodo informa il processo che una sessione sta ora debug del processo.

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
[in] Valore che identifica in modo univoco la sessione che si connette a questo processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'interfaccia passata deve essere considerata solo come un cookie, un valore che identifica in modo univoco la gestione del debug di sessione che si collega a questo processo. Nessuno dei metodi nell'interfaccia fornita è `pSession` funzionale.

## <a name="see-also"></a>Vedi anche
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
