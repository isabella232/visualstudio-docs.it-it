---
title: Proprietà IDebugProcessEx2::Detach . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7379436ae0da57d7f8c47ce8484c810a53a0a453
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723354"
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
[in] Valore che identifica in modo univoco la sessione da cui scollegare il processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 L'interfaccia `pSession` passata deve essere trattata solo come cookie, un valore che identifica in modo univoco il gestore di debug della sessione originariamente collegato a questo processo. nessuno dei metodi sull'interfaccia fornita è funzionale.

## <a name="see-also"></a>Vedere anche
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
