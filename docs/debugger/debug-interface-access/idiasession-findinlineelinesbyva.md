---
description: IDiaSession::findInlineeLinesByVA recupera un'enumerazione che consente a un client di scorrere le informazioni sul numero di riga di tutte le funzioni inline, direttamente o indirettamente, dal simbolo padre specificato e contenute nell'indirizzo virtuale specificato.
title: IDiaSession::findInlineeLinesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: dffe6594-e0d1-4ed5-aeea-8773f88d82a6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0a037733bc6291a2fbf41463f1097fbee97131a9fbc26c3b0e13504e723cf29f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344852"
---
# <a name="idiasessionfindinlineelinesbyva"></a>IDiaSession::findInlineeLinesByVA
Recupera un'enumerazione che consente a un client di scorrere le informazioni sul numero di riga di tutte le funzioni inline, direttamente o indirettamente, dal simbolo padre specificato e contenute all'interno dell'indirizzo virtuale specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findInlineeLinesByVA ( 
   IDiaSymbol*           parent,   ULONGLONG             va,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametri
 `parent`

[in] Oggetto `IDiaSymbol` che rappresenta l'elemento padre.

 `va`

[in] Specifica l'indirizzo come va va.

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
