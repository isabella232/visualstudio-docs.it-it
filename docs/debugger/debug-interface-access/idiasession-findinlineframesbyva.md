---
description: IDiaSession::findInlineFramesByVA recupera un'enumerazione che consente a un client di scorrere tutti i frame inline in un indirizzo virtuale specificato.
title: IDiaSession::findInlineFramesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: df9e68f6-e0a4-4cf6-b11d-61c40351e0cd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 56a4f01564bd6e8bcdb484fe06deceebb264b12b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629189"
---
# <a name="idiasessionfindinlineframesbyva"></a>IDiaSession::findInlineFramesByVA
Recupera un'enumerazione che consente a un client di scorrere tutti i frame inline in un indirizzo virtuale specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findInlineFramesByVA ( 
   IDiaSymbol*       parent,   ULONGLONG         va,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametri
 `parent`

[in] Oggetto `IDiaSymbol` che rappresenta l'elemento padre.

 `va`

[in] Specifica l'indirizzo come va va.

 `ppResult`

[out] Contiene un `IDiaEnumSymbols` oggetto che contiene l'elenco di frame recuperati.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
