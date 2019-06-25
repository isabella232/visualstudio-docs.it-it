---
title: IDiaLineNumber::get_length | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_length method
ms.assetid: 2c55a6f7-4ef5-45fb-9fd1-d72deaaa2829
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 896e26075780c0cbd7bf0b1762da141d5ba7d2d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828465"
---
# <a name="idialinenumbergetlength"></a>IDiaLineNumber::get_length
Recupera il numero di byte in un blocco.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_length ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il numero di byte in un blocco.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Il blocco è la lunghezza del codice sorgente nella riga come rappresentata dai [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) oggetto.

## <a name="see-also"></a>Vedere anche
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)