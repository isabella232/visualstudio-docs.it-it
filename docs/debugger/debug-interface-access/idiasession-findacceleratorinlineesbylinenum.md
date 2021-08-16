---
description: Restituisce un'enumerazione di simboli per i frame inline che corrispondono alla posizione di origine specificata.
title: IDiaSession::findAcceleratorInlineesByLinenum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: af45f71116d7a3c0ffcf51ea0bc81d44940f14fa6a0dd8a9833faa9c31980cb6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391920"
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
Restituisce un'enumerazione di simboli per i frame inline che corrispondono alla posizione di origine specificata.

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

[in] Oggetto `IDiaSymbol` che corrisponde alla funzione stub Accelerator in cui è necessario eseguire la ricerca.

 `file`

[in] Oggetto `IDiaSourceFile` del percorso di origine.

 `linenum`

[in] Numero di riga della posizione di origine.

 `colnum`

[in] Numero di colonna della posizione di origine.

 `ppResult`

[out] Puntatore a un `IDiaEnumLineNumbers` puntatore a interfaccia inizializzato con il risultato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
