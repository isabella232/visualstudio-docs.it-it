---
title: IDiaTable::get_Count | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::get_Count method
ms.assetid: bb47abe8-6706-4679-bc52-79f6444dae7e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ce325c51a9dfcee32093a0a1fafe82ea6a7fdd6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738743"
---
# <a name="idiatableget_count"></a>IDiaTable::get_Count
Recupera il numero di elementi nella tabella.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il numero di elementi nella tabella.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)