---
description: Restituisce un'enumerazione di simboli per i frame inline che corrispondono al percorso di origine specificato.
title: IDiaSession::findAcceleratorInlineesByLinenum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4ddb65e5041f19ad854eec271b22f3cbcab5a97c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147868"
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
Restituisce un'enumerazione di simboli per i frame inline che corrispondono al percorso di origine specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   IDiaSymbol*           parent,
   IDiaSourceFile*       file,
   DWORD                 linenum,
   DWORD                 colnum,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametri
 `parent`

in Oggetto `IDiaSymbol` che corrisponde alla funzione dello stub dell'acceleratore in cui è necessario eseguire la ricerca.

 `file`

in `IDiaSourceFile` Del percorso di origine.

 `linenum`

in Numero di riga del percorso di origine.

 `colnum`

in Numero di colonna del percorso di origine.

 `ppResult`

out Puntatore a un `IDiaEnumLineNumbers` puntatore a interfaccia inizializzato con il risultato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
