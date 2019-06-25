---
title: IDiaPropertyStorage::ReadULONGLONG | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6da509e226a612e80a10ca0759b5e264f31a1e13
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538681"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legge `ULONGLONG` valori in un set di proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `id`  
 [in] Identificatore della proprietà da leggere (`PROPID` definito in Wtypes. H come un `ULONG`).  
  
 `pValue`  
 [out] Restituisce il valore della proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_INVALIDARG` se la proprietà non è di tipo `ULONGLONG`.  
  
## <a name="remarks"></a>Note  
 Oggetto `ULONGLONG` è definito da Windows come un intero senza segno a 64 bit.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
