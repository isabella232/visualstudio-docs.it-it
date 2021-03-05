---
description: Recupera il file di origine e il numero di riga che indicano la posizione in cui è definito un tipo definito dall'utente specificato.
title: IDiaSymbol::getSrcLineOnTypeDefn | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: ad554d18-9988-4b64-ad71-e7594c266e94
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5d6288df169db6d0b5e0a0c31c674f398510f77c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161725"
---
# <a name="idiasymbolgetsrclineontypedefn"></a>IDiaSymbol::getSrcLineOnTypeDefn
Recupera il file di origine e il numero di riga che indicano la posizione in cui è definito un tipo definito dall'utente specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT getSrcLineOnTypeDefn(
   IDiaLineNumber **ppResult);
```

#### <a name="parameters"></a>Parametri
 `ppResult`

out `IDiaLineNumber` Oggetto contenente il file di origine e il numero di riga in cui è definito dall'utente.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
