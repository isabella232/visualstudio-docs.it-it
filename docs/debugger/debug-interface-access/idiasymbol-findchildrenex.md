---
description: Recupera gli elementi figlio del simbolo. I simboli locali restituiti includono informazioni sull'intervallo dinamico, se il programma viene compilato con l'ottimizzazione.
title: IDiaSymbol::findChildrenEx | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenEx
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c23788815590f5122191cc3db7190cfb9581e1c8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091128"
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
Recupera gli elementi figlio del simbolo. I simboli locali restituiti includono informazioni sull'intervallo dinamico, se il programma viene compilato con l'ottimizzazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findChildrenEx ( 
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

[in] Specifica le opzioni di confronto da applicare alla corrispondenza dei nomi. I valori [dell'enumerazione NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md) possono essere usati da soli o in combinazione.

 `ppResult`

[out] Restituisce un [oggetto IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) che contiene un elenco dei simboli figlio recuperati.

## <a name="return-value"></a>Valore restituito
 Restituisce se è stato trovato almeno un elemento figlio del simbolo oppure restituisce se non sono stati trovati elementi figlio. In caso `S_OK` `S_FALSE` contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo è la versione estesa di [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md).

## <a name="requirements"></a>Requisiti
 Intestazione: Dia2.h

 Libreria: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
