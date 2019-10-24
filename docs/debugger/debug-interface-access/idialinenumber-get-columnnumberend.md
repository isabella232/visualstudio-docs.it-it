---
title: IDiaLineNumber::get_columnNumberEnd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4433bc243a7a4f5352f0476370853572be8ddd38
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743243"
---
# <a name="idialinenumberget_columnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
Recupera il numero della colonna di origine in base 1 in cui termina l'espressione o l'istruzione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_columnNumberEnd ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il numero di colonna in cui termina l'espressione o l'istruzione. Se il valore è zero, le informazioni sull'estremità della colonna non sono presenti.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Il valore della colonna restituito da questo metodo è un offset di byte nella riga alla posizione dopo l'ultimo carattere dell'istruzione sulla riga.

## <a name="see-also"></a>Vedere anche
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)