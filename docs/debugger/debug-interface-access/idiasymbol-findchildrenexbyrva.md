---
title: IDiaSymbol::findChildrenExByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByRVA
ms.assetid: cbc57c6c-7d64-4469-a114-1dd6671e5ec5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b2ef64d288bdb8e6e5a7cf8befa1f6d7c90ecf0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863704"
---
# <a name="idiasymbolfindchildrenexbyrva"></a>IDiaSymbol::findChildrenExByRVA
Recupera gli elementi figlio del simbolo validi in corrispondenza dell'indirizzo RVA (relativo Virtual Address) specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findChildrenExByRVA ( 
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

in Specifica l'RVA.

 `ppResult`

out Restituisce un oggetto [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) che contiene un elenco dei simboli figlio recuperati.

## <a name="return-value"></a>Valore restituito
 Restituisce `S_OK` se è stato trovato almeno un elemento figlio del simbolo oppure restituisce `S_FALSE` se non sono stati trovati elementi figlio; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 I simboli locali restituiti includono informazioni sull'intervallo Live.

## <a name="requirements"></a>Requisiti
 Intestazione: dia2. h

 Libreria: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)