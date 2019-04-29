---
title: IDebugProcessEx2::Detach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e736c14b1a87188f45658a51cff0c123553332e9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917502"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Questo metodo indica il processo che una sessione di debug non è più il processo.

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

#### <a name="parameters"></a>Parametri
 `pSession`

 [in] Un valore che identifica in modo univoco la sessione per questo processo da scollegare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 L'interfaccia passato `pSession` è deve essere considerato solo un cookie, un valore che identifica in modo univoco il gestore di sessione di debug che originariamente collegato a questo processo, nessuno dei metodi nell'interfaccia specificata sono funzionali.

## <a name="see-also"></a>Vedere anche
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)