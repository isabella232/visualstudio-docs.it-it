---
description: Recupera le informazioni sul numero di riga per le righe contenute in un intervallo di indirizzi virtuali (VA) specificato.
title: IDiaSession::findLinesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: cd4d27c96a6a08c6fc63d38d9845d30366be760c7db9e5fd34dfac55fc9ae497
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380141"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
Recupera le informazioni sul numero di riga per le righe contenute in un intervallo di indirizzi virtuali (VA) specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findLinesByVA (
    ULONGLONG             va,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametri
`va`

[in] Specifica l'indirizzo come va.

`length`

[in] Specifica il numero di byte dell'intervallo di indirizzi da coprire con questa query.

`ppResult`

[out] Restituisce un [oggetto IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) che contiene un elenco di tutti i numeri di riga che coprono l'intervallo di indirizzi specificato.

## <a name="example"></a>Esempio
Questo esempio mostra una funzione che ottiene tutti i numeri di riga contenuti in una funzione usando l'indirizzo virtuale e la lunghezza della funzione.

```C++
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    ULONGLONG            va;
    ULONGLONG            length;

    if (pFunc->get_virtualAddress ( &va ) == S_OK)
    {
        pFunc->get_length( &length );
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>Vedi anche
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
