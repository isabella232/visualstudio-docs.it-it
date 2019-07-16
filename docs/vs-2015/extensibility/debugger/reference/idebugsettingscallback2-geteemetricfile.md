---
title: IDebugSettingsCallback2::GetEEMetricFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricFile
ms.assetid: 3a0bf9e5-bbd2-4d15-840d-8244732787fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b7822bcabbe2f283c25a3e22f1e650269e7e62
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155197"
---
# <a name="idebugsettingscallback2geteemetricfile"></a>IDebugSettingsCallback2::GetEEMetricFile
Recupera il file di metrica dell'analizzatore di espressioni espressione stato assegnato il nome o la metrica.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetEEMetricFile(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   BSTR*   pbstrValue
);
```

```csharp
private int GetEEMetricFile(
   ref Guid   guidLang,
   ref Guid   guidVendor,
   string     pszMetric,
   out string pbstrValue
);
```

#### <a name="parameters"></a>Parametri
 `guidLang`

 [in] Identificatore univoco del linguaggio di programmazione.

 `guidVendor`

 [in] Identificatore univoco del fornitore.

 `pszMetric`

 [in] Nome della metrica.

 `pbstrValue`

 [out] Restituisce il contenuto del file metrica sotto forma di stringa.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)