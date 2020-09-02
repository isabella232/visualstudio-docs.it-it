---
title: IDiaSymbol::findInlineeLinesByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: f1ab47ca-c851-48ea-9c12-47fb80b31102
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ea271ae921ebefe9c579a89b487a6f96c014f1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464548"
---
# <a name="idiasymbolfindinlineelinesbyaddr"></a>IDiaSymbol::findInlineeLinesByAddr
Recupera un'enumerazione che consente a un client di scorrere le informazioni sul numero di riga di tutte le funzioni inline, direttamente o indirettamente, in questo simbolo all'interno dell'intervallo di indirizzi specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findInlineeLinesByAddr ( 
   DWORD                 isect,
   DWORD                 offset,
   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametri
 `isect`

in Specifica il componente della sezione dell'indirizzo.

 `offset`

in Specifica il componente di offset dell'indirizzo.

 `length`

in Specifica l'intervallo di indirizzi, in numero di byte, per coprire la query.

 `ppResult`

out Contiene un `IDiaEnumLineNumbers` oggetto che contiene l'elenco dei numeri di riga recuperati.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)