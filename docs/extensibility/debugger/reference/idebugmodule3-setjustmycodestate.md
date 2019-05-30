---
title: IDebugModule3::SetJustMyCodeState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::SetJustMyCodeState
helpviewer_keywords:
- IDebugModule3::SetJustMyCodeState
ms.assetid: 68f8166d-ef64-49ae-ad5e-79604f43bbd4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46a200b91e1680da3f7beac1b0ec4856a39b2564
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323806"
---
# <a name="idebugmodule3setjustmycodestate"></a>IDebugModule3::SetJustMyCodeState
Contrassegna il modulo o non come codice utente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetJustMyCodeState(
   BOOL fIsUserCode
);
```

```csharp
int SetJustMyCodeState(
   int fIsUserCode
);
```

## <a name="parameters"></a>Parametri
`fIsUserCode`\
[in] Diverso da zero (`TRUE`) se il modulo deve essere considerato codice utente, zero (`FALSE`) in caso contrario.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)