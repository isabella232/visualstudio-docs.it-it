---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07c9c5d129305d8c3128a081abe8079321043a57
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53918953"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Recupera i nomi di stringa corrispondente assegnato gli identificatori di proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cpropid`  
 [in] Numero di ID proprietà nel `rgpropid`.  
  
 `rgpropid`  
 [in] Matrice di ID proprietà per cui ottenere i nomi (`PROPID` definito in Wtypes. H come un `ULONG`).  
  
 `rglpwstrName`  
 [in, out] Matrice di nomi di proprietà per l'ID di proprietà specificato. La matrice deve essere preallocata per contenere il numero di nomi di proprietà richiesto e deve essere in grado di contenere almeno `cpropid``BSTR` stringhe.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 I nomi di proprietà restituito devono essere liberati (chiamando il `SysFreeString` funzioni) quando non sono più necessari.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)