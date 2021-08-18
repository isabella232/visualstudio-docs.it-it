---
description: IDiaSymbol::findInlineFramesByRVA recupera un'enumerazione che consente a un client di scorrere tutti i frame inline in un indirizzo virtuale relativo (RVA) specificato.
title: IDiaSymbol::findInlineFramesByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: e7a6d9cb-2726-4ac7-9f38-415ad215bf9c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ce4ae1bdafd5189f40d780fa17550d9113e33bb4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091068"
---
# <a name="idiasymbolfindinlineframesbyrva"></a>IDiaSymbol::findInlineFramesByRVA
Recupera un'enumerazione che consente a un client di scorrere tutti i frame inline in un indirizzo virtuale relativo specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findInlineFramesByRVA (    DWORD             rva,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametri
 `rva`

[in] Specifica l'indirizzo come RVA.

 `ppResult`

[out] Contiene un `IDiaEnumSymbols` oggetto che contiene l'elenco di frame recuperati.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
