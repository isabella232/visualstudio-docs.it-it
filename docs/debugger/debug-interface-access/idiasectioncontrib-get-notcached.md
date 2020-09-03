---
title: IDiaSectionContrib::get_notCached | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_notCached method
ms.assetid: 5408ea53-f64c-431e-9f62-62819026b038
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47a7c0703568d044bcda93fde7c9ecee0dea52a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466210"
---
# <a name="idiasectioncontribget_notcached"></a>IDiaSectionContrib::get_notCached
Recupera un flag che indica se la sezione non può essere memorizzata nella cache.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_notCached ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce `TRUE` se la sezione non può essere memorizzata nella cache; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)