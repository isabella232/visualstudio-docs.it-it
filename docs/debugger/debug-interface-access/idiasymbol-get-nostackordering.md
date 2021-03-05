---
description: Questa funzione recupera un flag che indica se non è stato possibile eseguire l'ordinamento dello stack come parte del controllo del buffer dello stack (opzione del compilatore[/GS (controllo di sicurezza del buffer)](/cpp/build/reference/gs-buffer-security-check) ).
title: IDiaSymbol::get_noStackOrdering | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noStackOrdering method
ms.assetid: a1753917-705b-4165-9880-d05e91e6dcb4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fbfcb8c4404179431c4c480ee036210cb2d0be77
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147162"
---
# <a name="idiasymbolget_nostackordering"></a>IDiaSymbol::get_noStackOrdering
Questa funzione recupera un flag che indica se non è stato possibile eseguire l'ordinamento dello stack come parte del controllo del buffer dello stack (opzione del compilatore[/GS (controllo di sicurezza del buffer)](/cpp/build/reference/gs-buffer-security-check) ).

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_noStackOrdering(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce `TRUE` se non è stato possibile eseguire l'ordinamento dello stack come parte del controllo del buffer dello stack; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/GS (controllo sicurezza buffer)](/cpp/build/reference/gs-buffer-security-check)
