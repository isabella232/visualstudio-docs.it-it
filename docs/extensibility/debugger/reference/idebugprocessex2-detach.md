---
description: Questo metodo informa il processo che una sessione non esegue più il debug del processo.
title: IDebugProcessEx2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f67ba1d07e1b92ed80e330ee279130061d0a647e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057564"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Questo metodo informa il processo che una sessione non esegue più il debug del processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parametri
`pSession`\
[in] Valore che identifica in modo univoco la sessione da cui disconnettere il processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'interfaccia passata deve essere considerata solo come un cookie, un valore che identifica in modo univoco la gestione del debug di sessione originariamente associata a questo processo. Nessuno dei metodi nell'interfaccia fornita è `pSession` funzionale.

## <a name="see-also"></a>Vedi anche
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
