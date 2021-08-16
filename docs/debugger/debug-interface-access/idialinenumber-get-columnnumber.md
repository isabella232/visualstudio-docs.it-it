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
ms.openlocfilehash: 1cad0c103b61c8b50e5b10f7a63c13f6bda015ade0cb11903c0e730db9ca2e5a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121392192"
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
