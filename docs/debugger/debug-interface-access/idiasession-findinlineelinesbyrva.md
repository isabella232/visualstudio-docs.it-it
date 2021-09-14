---
description: IDiaSession::findInlineeLinesByRVA recupera un'enumerazione che consente a un client di scorrere le informazioni sul numero di riga di tutte le funzioni inline, direttamente o indirettamente, dal simbolo padre specificato e contenute nell'indirizzo RVA (Relative Virtual Address) specificato.
title: IDiaSession::findInlineeLinesByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 7a74d5ee-0dbf-47c0-92b4-47ec03b13ce9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1bb42c5d1ffed49c8bff3a6bc23f20f3cb9c86d5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629219"
---
# <a name="idiasessionfindinlineelinesbyrva"></a>IDiaSession::findInlineeLinesByRVA
Recupera un'enumerazione che consente a un client di scorrere le informazioni sul numero di riga di tutte le funzioni inline, direttamente o indirettamente, dal simbolo padre specificato e contenute all'interno dell'indirizzo RVA (Relative Virtual Address) specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findInlineeLinesByRVA ( 
   IDiaSymbol*           parent,
   DWORD                 rva,
   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametri
 `parent`

[in] Oggetto `IDiaSymbol` che rappresenta l'elemento padre.

 `rva`

[in] Specifica l'indirizzo come RVA.

 `length`

[in] Specifica l'intervallo di indirizzi, in numero di byte, da coprire con questa query.

 `ppResult`

[out] Contiene un `IDiaEnumLineNumbers` oggetto che contiene l'elenco di numeri di riga recuperati.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
