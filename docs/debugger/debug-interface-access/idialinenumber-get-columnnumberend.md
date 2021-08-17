---
description: Recupera il numero di colonna di origine in base uno in cui termina l'espressione o l'istruzione.
title: IDiaLineNumber::get_columnNumberEnd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 19e3ed60a17abdb39e9027455fc4e96bcad3a32a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122066598"
---
# <a name="idialinenumberget_columnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
Recupera il numero di colonna di origine in base uno in cui termina l'espressione o l'istruzione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_columnNumberEnd ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il numero di colonna in cui termina l'espressione o l'istruzione. Se il valore è zero, le informazioni sull'estremità della colonna non sono presenti.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Il valore della colonna restituito da questo metodo è un offset di byte nella riga nella posizione successiva all'ultimo carattere dell'istruzione nella riga.

## <a name="see-also"></a>Vedi anche
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
