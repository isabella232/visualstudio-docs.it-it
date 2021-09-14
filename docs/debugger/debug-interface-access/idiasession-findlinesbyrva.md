---
description: Recupera le righe in un compilando specificato che contengono un indirizzo virtuale relativo (RVA) specificato.
title: IDiaSession::findLinesByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByRVA method
ms.assetid: 06f53b0b-b5b4-42cf-9252-dcee0dbe2d71
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 89731647fa1de03d5ad3ae94b0357555d525de9c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629171"
---
# <a name="idiasessionfindlinesbyrva"></a>IDiaSession::findLinesByRVA
Recupera le righe in un compilando specificato che contengono un indirizzo virtuale relativo (RVA) specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findLinesByRVA ( 
    DWORD                 rva,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametri
`rva`

[in] Specifica l'indirizzo come RVA.

`length`

[in] Specifica il numero di byte dell'intervallo di indirizzi da coprire con questa query.

`ppResult`

[out] Restituisce un [oggetto IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) che contiene un elenco di tutti i numeri di riga che coprono l'intervallo di indirizzi specificato.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="example"></a>Esempio
Questo esempio mostra una funzione che ottiene tutti i numeri di riga contenuti nella funzione specificata usando l'indirizzo virtuale e la lunghezza relativi della funzione.

```C++
IDiaEnumLineNumbers* GetLineNumbersByRVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    DWORD                rva;
    ULONGLONG            length;

    if (pFunc->get_relativeVirtualAddress ( &rva ) == S_OK)
    {
        pFunc->get_length ( &length );
        pSession->findLinesByRVA( rva, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>Vedi anche
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
