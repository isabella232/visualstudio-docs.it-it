---
title: IDiaSymbol::findChildrenExByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByVA
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9cc9f540b200ff6fdf4736b6a0bf64175a5ee3e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741248"
---
# <a name="idiasymbolfindchildrenexbyva"></a>IDiaSymbol::findChildrenExByVA
Recupera gli elementi figlio del simbolo validi in corrispondenza di un indirizzo virtuale specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findChildrenExByVA ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   DWORD             address,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametri
 `symtag`

in Specifica i tag dei simboli degli elementi figlio da recuperare, come definito nell' [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md). Impostare su `SymTagNull` per tutti gli elementi figlio da recuperare.

 `name`

in Specifica il nome degli elementi figlio da recuperare. Impostare su `NULL` per tutti gli elementi figlio da recuperare.

 `compareFlags`

in Specifica le opzioni di confronto da applicare alla corrispondenza dei nomi. I valori dell'enumerazione [NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) possono essere usati singolarmente o in combinazione.

 `address`

in Specifica l'indirizzo virtuale.

 `ppResult`

out Restituisce un oggetto [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) che contiene un elenco dei simboli figlio recuperati.

## <a name="return-value"></a>Valore restituito
 Restituisce `S_OK` se è stato trovato almeno un elemento figlio del simbolo oppure restituisce `S_FALSE` se non sono stati trovati elementi figlio; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 I simboli locali restituiti includono informazioni sull'intervallo Live.

## <a name="requirements"></a>Requisiti
 Intestazione: dia2. h

 Libreria: diaguids. lib

 DLL: msdia100. dll

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)