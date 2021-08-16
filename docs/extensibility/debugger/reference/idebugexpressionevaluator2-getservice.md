---
description: Recupera un oggetto servizio in base al relativo identificatore univoco.
title: IDebugExpressionEvaluator2::GetService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34a432be96d0511128a5466c2fd771f0682129bb3ddf4087a129831ace8be491
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360430"
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
[in] Identificatore univoco del servizio da recuperare.

`ppService`\
[out] Restituisce un oggetto che rappresenta il servizio.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Può essere utilizzato da un analizzatore di espressioni di terze parti per ottenere servizi da un altro analizzatore di espressioni. Ad esempio, questo metodo può essere usato per ottenere l'interfaccia per il servizio visualizzatore dall'analizzatore di espressioni predefinito. È improbabile che gli analizzatori di espressioni di terze parti implementino questa interfaccia.

## <a name="see-also"></a>Vedi anche
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
