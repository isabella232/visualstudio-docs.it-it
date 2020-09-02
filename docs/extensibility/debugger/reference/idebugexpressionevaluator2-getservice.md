---
title: 'IDebugExpressionEvaluator2:: GetService | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729357"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Recupera un oggetto servizio in base al relativo identificatore univoco.

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
in Identificatore univoco del servizio da recuperare.

`ppService`\
out Restituisce un oggetto che rappresenta il servizio.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questa operazione può essere utilizzata da un analizzatore di espressioni di terze parti per ottenere i servizi da un altro analizzatore di espressioni. Questo metodo, ad esempio, può essere utilizzato per ottenere l'interfaccia per il servizio Visualizzatore dall'analizzatore di espressioni predefinito. È improbabile che gli analizzatori di espressioni di terze parti debbano implementare questa interfaccia.

## <a name="see-also"></a>Vedere anche
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
