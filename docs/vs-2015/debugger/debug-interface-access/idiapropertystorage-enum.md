---
title: IDiaPropertyStorage::Enum | Microsoft Docs
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
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a92f0dc6d8ffff0a9dab397c348008454920d56
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216775"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ottiene un enumeratore per le proprietà all'interno di questo set.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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



