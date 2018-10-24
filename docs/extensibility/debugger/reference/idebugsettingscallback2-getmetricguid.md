---
title: IDebugSettingsCallback2::GetMetricGuid | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricGuid
ms.assetid: 91092763-3362-4857-adf0-231bc1254206
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d7b45d5126f1fc437f54ed028ae7f2f5535c207
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831146"
---
# <a name="idebugsettingscallback2getmetricguid"></a>IDebugSettingsCallback2::GetMetricGuid
Recupera l'identificatore univoco di una metrica in base al nome.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetMetricGuid(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   GUID*   pguidValue  
);  
```  
  
```csharp  
private int GetMetricGuid(  
   string   pszType,  
   ref Guid guidSection,  
   string   pszMetric,  
   out Guid pguidValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszType`  
 [in] Tipo di metrica.  
  
 `guidSection`  
 [in] Identificatore univoco della sezione.  
  
 `pszMetric`  
 [in] Nome della metrica.  
  
 `pguidValue`  
 [out] Restituisce l'identificatore univoco della metrica.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)