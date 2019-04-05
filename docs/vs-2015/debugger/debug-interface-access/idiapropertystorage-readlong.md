---
title: IDiaPropertyStorage::ReadLONG | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08661272bea779ff0789619d58bf6f2837a21917
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968054"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legge `LONG` valori in un set di proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `id`  
 [in] Identificatore della proprietà da leggere (`PROPID` definito in Wtypes. H come un `ULONG`).  
  
 `pValue`  
 [out] Restituisce il valore della proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_INVALIDARG` se la proprietà non è di tipo `LONG`.  
  
## <a name="remarks"></a>Note  
 Oggetto `LONG` è definito da Windows come un intero con segno a 32 bit.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
