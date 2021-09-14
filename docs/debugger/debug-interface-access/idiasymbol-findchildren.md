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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 72bd4479c50c6a518f4087c2244b2e194f5f05d5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628932"
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

[in] Specifica i tag dei simboli degli elementi figlio da recuperare, come definito [nell'enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md). Impostare su `SymTagNull` per recuperare tutti gli elementi figlio.

 `name`

[in] Specifica il nome degli elementi figlio da recuperare. Impostare su `NULL` per recuperare tutti gli elementi figlio.

 `compareFlags`

[in] Specifica le opzioni di confronto applicate alla corrispondenza dei nomi. I valori [dell'enumerazione NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md) possono essere usati da soli o in combinazione.

 `ppResult`

[out] Restituisce un [oggetto IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) che contiene un elenco dei simboli figlio recuperati.

## <a name="return-value"></a>Valore restituito
 Restituisce se è stato trovato almeno un elemento figlio del simbolo oppure restituisce se non sono stati trovati elementi `S_OK` `S_FALSE` figlio. In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo è identico alla chiamata al [metodo IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) con questo simbolo come primo parametro.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
