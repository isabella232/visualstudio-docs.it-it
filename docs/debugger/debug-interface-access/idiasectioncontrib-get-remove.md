---
title: IDiaSectionContrib::get_remove | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_remove method
ms.assetid: fd30ab7b-022b-4402-a42a-2d38e274c1b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01b3eef646f9105d651a17b58100aad8b4869c3c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827664"
---
# <a name="idiasectioncontribgetremove"></a>IDiaSectionContrib::get_remove
Recupera un flag che indica se la sezione è stato rimosso prima di renderlo parte dell'immagine in memoria.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_remove ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se la sezione non devono essere aggiunti all'immagine in memoria; in caso contrario, restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)