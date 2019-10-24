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
ms.openlocfilehash: 2f803fac1439d384133f0819859f2917072a8790
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743188"
---
# <a name="idialinenumberget_length"></a>IDiaLineNumber::get_length
Recupera il numero di byte in un blocco.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_length ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il numero di byte in un blocco.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Il blocco è la lunghezza del codice sorgente sulla riga come rappresentato dall'oggetto [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) .

## <a name="see-also"></a>Vedere anche
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)