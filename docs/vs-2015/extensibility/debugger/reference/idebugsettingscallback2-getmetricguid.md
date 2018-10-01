---
title: IDebugSettingsCallback2::GetMetricGuid | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricGuid
ms.assetid: 91092763-3362-4857-adf0-231bc1254206
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 48662b00dc168e44e6d1c8e5fb473e716e423304
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530473"
---
# <a name="idebugsettingscallback2getmetricguid"></a>IDebugSettingsCallback2::GetMetricGuid
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugSettingsCallback2::GetMetricGuid](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugsettingscallback2-getmetricguid).  
  
Recupera l'identificatore univoco di una metrica in base al nome.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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

