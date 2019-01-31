---
title: IDiaPropertyStorage::Enum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0244aca54ffe7b68ea4cfd82be465c28524758ff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54973486"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Ottiene un enumeratore per le proprietà all'interno di questo set.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppenum`  
 [out] Restituisce un `IEnumSTATPROPSTG` oggetto (nello spazio dei nomi Interop) che rappresenta un'enumerazione delle proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)