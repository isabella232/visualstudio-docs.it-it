---
title: Proprietà IDebugExpressionEvaluator2::GetService . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5428606ad54c7938037c3ffecf04f1cfe41787c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729357"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Recupera un oggetto servizio dato il relativo identificatore univoco.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

## <a name="parameters"></a>Parametri
`uid`\
[in] Identificatore univoco del servizio da recuperare.

`ppService`\
[fuori] Restituisce un oggetto che rappresenta il servizio.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo può essere utilizzato da un analizzatore di espressioni di terze parti per ottenere servizi da un altro analizzatore di espressioni. Ad esempio, questo metodo può essere utilizzato per ottenere l'interfaccia per il servizio visualizzatore dall'analizzatore di espressioni predefinito. È improbabile che gli analizzatori di espressioni di terze parti debbano implementare questa interfaccia.

## <a name="see-also"></a>Vedere anche
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
