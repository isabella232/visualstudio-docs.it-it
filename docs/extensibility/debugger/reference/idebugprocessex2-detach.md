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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58480e52e86fc4603648d9f534cb03e944a8dde8
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212894"
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

## <a name="parameters"></a>Parametri
`pSession`\
[in] Un valore che identifica in modo univoco la sessione per questo processo da scollegare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 L'interfaccia passato `pSession` è deve essere considerato solo un cookie, un valore che identifica in modo univoco il gestore di sessione di debug che originariamente collegato a questo processo, nessuno dei metodi nell'interfaccia specificata sono funzionali.

## <a name="see-also"></a>Vedere anche
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)