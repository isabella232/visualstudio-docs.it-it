---
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64eee421a5ed5bd46a64b51694d913a4f2dc4d41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538876"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legge `BOOL` i valori in un set di proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `id`  
 in Identificatore della proprietà da leggere ( `PROPID` è definito in Wtypes. h come `ULONG` ).  
  
 `pValue`  
 out Restituisce il valore della proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore. Restituisce `E_INVALIDARG` se la proprietà non è di tipo `BOOL` .  
  
## <a name="remarks"></a>Osservazioni  
 Per risultati coerenti, interpretare il `BOOL` valore in modo che i valori diversi da zero siano `TRUE` e zero sia `FALSE` .  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
