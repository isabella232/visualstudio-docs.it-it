---
title: IDebugSettingsCallback2::GetEEMetricGuid | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricGuid
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7662d5c99225a9d9d0ab61883a993bb968e73cdf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54964509"
---
# <a name="idebugsettingscallback2geteemetricguid"></a>IDebugSettingsCallback2::GetEEMetricGuid
Recupera l'identificatore univoco per una metrica dell'analizzatore di espressioni in base al nome.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetEEMetricGuid(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   GUID*   pguidValue  
);  
```  
  
```csharp  
HRESULT GetEEMetricGuid(  
   ref Guid guidLang,  
   ref Guid guidVendor,  
   string   pszMetric,  
   out Guid pguidValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidLang`  
 [in] Identificatore univoco del linguaggio di programmazione.  
  
 `guidVendor`  
 [in] Identificatore univoco del fornitore.  
  
 `pszMetric`  
 [in] Nome della metrica.  
  
 `pguidValue`  
 [out] Restituisce l'identificatore univoco della metrica.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)