---
title: IDiaSectionContrib::get_addressSection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_addressSection method
ms.assetid: 13fe7e0b-c978-4a1d-bb57-64c8583b5e14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ccca5decf432169add7ebf6d70a33fe6b5c1c9e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742765"
---
# <a name="idiasectioncontribget_addresssection"></a>IDiaSectionContrib::get_addressSection
Recupera la parte della sezione dell'indirizzo del contributo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce la parte della sezione dell'indirizzo del contributo.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)