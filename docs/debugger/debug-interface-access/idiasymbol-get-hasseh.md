---
title: IDiaSymbol::get_hasSEH | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e96216b5e33031405df3b01a3f76412a544bb51
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740443"
---
# <a name="idiasymbolget_hasseh"></a>IDiaSymbol::get_hasSEH
Recupera un flag che specifica se la funzione contiene una [gestione strutturata delle eccezioni (C++C/)](/cpp/cpp/structured-exception-handling-c-cpp) (ad esempio, blocchi __try/\__except).

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_hasSEH(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

out Restituisce `TRUE` se la funzione presenta blocchi di gestione delle eccezioni strutturati. in caso contrario, restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisiti|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Gestione strutturata delle eccezioni (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp)