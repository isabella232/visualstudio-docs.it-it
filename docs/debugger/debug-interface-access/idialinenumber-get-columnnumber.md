---
description: Recupera il numero di colonna in cui inizia l'espressione o l'istruzione.
title: IDiaLineNumber::get_columnNumber | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumber method
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: dc09fa2761b6048219afc9af4ac2e1ce917a2601
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629705"
---
# <a name="idialinenumberget_columnnumber"></a>IDiaLineNumber::get_columnNumber
Recupera il numero di colonna in cui inizia l'espressione o l'istruzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT get_columnNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il numero di colonna in cui inizia l'espressione o l'istruzione. Se il valore è zero, le informazioni sulla colonna non sono presenti.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Il valore della colonna restituito da questo metodo è un offset di byte nella riga al primo carattere dell'istruzione nella riga.

## <a name="see-also"></a>Vedi anche
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
