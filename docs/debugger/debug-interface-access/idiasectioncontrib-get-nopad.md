---
title: IDiaSectionContrib::get_nopad | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a81113242379070e56d6d0bd0f916355985eaa42
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742615"
---
# <a name="idiasectioncontribget_nopad"></a>IDiaSectionContrib::get_nopad
Recupera un flag che indica se la sezione non deve essere riempita al limite di memoria successivo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_nopad(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce `TRUE` se la sezione non deve essere riempita al limite di memoria successivo. in caso contrario, restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Si tratta di una proprietà in genere visibile solo in file meno recenti.

## <a name="see-also"></a>Vedere anche
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)