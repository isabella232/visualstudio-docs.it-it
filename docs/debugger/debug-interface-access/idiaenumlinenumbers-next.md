---
description: Recupera un numero specificato di numeri di riga nella sequenza di enumerazione.
title: IDiaEnumLineNumbers::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Next method
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0c114955909619ffba09b44c3f8bf2380530dc79
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134436"
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
Recupera un numero specificato di numeri di riga nella sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaLineNumber** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>Parametri
 celt

[in] Numero di numeri di riga nell'enumeratore da recuperare.

 Rgelt

[out] Restituisce una matrice di [oggetti IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) che rappresentano i numeri di riga desiderati.

 pceltFetched

[out] Restituisce il numero di righe nell'enumeratore recuperato.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti altri numeri di riga. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
