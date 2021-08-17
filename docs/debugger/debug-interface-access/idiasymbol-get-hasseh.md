---
description: Recupera un flag che specifica se la funzione contiene una gestione delle eccezioni strutturata (C/C++)), ad esempio blocchi _try/__except.
title: IDiaSymbol::get_hasSEH | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 821336057b3530ad2b46c9f14c6b04669b7db983
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052261"
---
# <a name="idiasymbolget_hasseh"></a>IDiaSymbol::get_hasSEH
Recupera un flag che specifica se la funzione contiene una gestione delle eccezioni strutturata [(C/C++),](/cpp/cpp/structured-exception-handling-c-cpp) ad esempio blocchi \_ __try/_except strutturati.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_hasSEH(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

[out] Restituisce `TRUE` se la funzione ha blocchi di gestione delle eccezioni strutturati; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o codice `S_FALSE` di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Structured Exception Handling (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp)
