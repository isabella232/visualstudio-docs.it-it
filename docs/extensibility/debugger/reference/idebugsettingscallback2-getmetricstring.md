---
description: Recupera la stringa di valore della metrica in base al nome.
title: 'IDebugSettingsCallback2:: GetMetricString | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricString
- GetMetricString
ms.assetid: ecc875a2-8ac6-444c-a839-5191a780fd6b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f166c9b3cfce60f8800ddd2bf88d5c35b8e606db
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071272"
---
# <a name="idebugsettingscallback2getmetricstring"></a>IDebugSettingsCallback2::GetMetricString
Recupera la stringa di valore della metrica in base al nome.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetMetricString(
    LPCWSTR pszType,
    REFGUID guidSection,
    LPCWSTR pszMetric,
    BSTR*   pbstrValue
);
```

```csharp
private int GetMetricString(
    string     pszType,
    ref Guid   guidSection,
    string     pszMetric,
    out string pbstrValue
);
```

## <a name="parameters"></a>Parametri
`pszType`\
in Tipo della metrica.

`guidSection`\
in Identificatore univoco della sezione.

`pszMetric`\
in Nome della metrica.

`pbstrValue`\
out Restituisce la stringa di valore della metrica.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
