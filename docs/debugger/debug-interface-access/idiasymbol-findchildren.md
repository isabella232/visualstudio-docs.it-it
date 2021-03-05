---
description: Recupera gli elementi figlio del simbolo.
title: IDiaSymbol::findChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 809157c8ffd4b3955b7a8d7b079f63398437e35c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161173"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
Recupera gli elementi figlio del simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findChildren ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametri
 `symtag`

in Specifica i tag dei simboli degli elementi figlio da recuperare, come definito nell' [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md). Impostare su `SymTagNull` per tutti gli elementi figlio da recuperare.

 `name`

in Specifica il nome degli elementi figlio da recuperare. Impostare su `NULL` per tutti gli elementi figlio da recuperare.

 `compareFlags`

in Specifica le opzioni di confronto applicate alla corrispondenza dei nomi. I valori dell'enumerazione [NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) possono essere usati singolarmente o in combinazione.

 `ppResult`

out Restituisce un oggetto [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) che contiene un elenco dei simboli figlio recuperati.

## <a name="return-value"></a>Valore restituito
 Restituisce `S_OK` se è stato trovato almeno un elemento figlio del simbolo oppure restituisce `S_FALSE` se non sono stati trovati elementi figlio; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo è identico alla chiamata al metodo [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) con questo simbolo come primo parametro.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
