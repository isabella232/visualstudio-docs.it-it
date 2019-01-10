---
title: Idiaenumdebugstreamdata | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::get__NewEnum method
ms.assetid: 023b3e31-0fc9-478d-88e8-af2ce762f322
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee7e7d79bd1c4bef46ddf61fe7ad10aa483a0bef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871518"
---
# <a name="idiaenumdebugstreamdatagetnewenum"></a>IDiaEnumDebugStreamData::get__NewEnum
Recupera il <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione l'enumeratore.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pRetVal  
 [out] Restituisce il `IUnknown` interfaccia che rappresenta il <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione l'enumeratore.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)