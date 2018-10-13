---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4dd1027d5921af482a71c7c45e5b6c90599df512
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232830"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera i nomi di stringa corrispondente assegnato gli identificatori di proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
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



