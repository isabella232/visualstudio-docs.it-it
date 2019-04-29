---
title: IDiaSectionContrib::get_informational | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_informational method
ms.assetid: 5351e89f-7db1-4f8e-9e57-2dd1c74002e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b00d07b788fe07fbe2e879f01a98929927743a0b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839589"
---
# <a name="idiasectioncontribgetinformational"></a>IDiaSectionContrib::get_informational
Recupera un flag che indica se una sezione contiene informazioni simili o commenti.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_informational(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se la sezione contiene i commenti o altre informazioni; in caso contrario restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 La sezione .directive contiene in genere informazioni.

## <a name="see-also"></a>Vedere anche
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)