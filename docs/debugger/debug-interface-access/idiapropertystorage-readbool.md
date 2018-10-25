---
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3df4ce44c0cf0b3b09442dc695f73c415035e84a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904180"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
Legge `BOOL` valori in un set di proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `id`  
 [in] Identificatore della proprietà da leggere (`PROPID` definito in Wtypes. H come un `ULONG`).  
  
 `pValue`  
 [out] Restituisce il valore della proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_INVALIDARG` se la proprietà non è di tipo `BOOL`.  
  
## <a name="remarks"></a>Note  
 Per ottenere risultati coerenti, interpretare la `BOOL` valore in modo che siano valori diversi da zero `TRUE` e zero è `FALSE`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)