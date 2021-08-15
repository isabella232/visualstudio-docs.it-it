---
description: Recupera un flag che specifica se la funzione ha l'attributo naked, ovvero se la funzione non ha codice di prologo o epilogo aggiunto dal compilatore.
title: IDiaSymbol::get_isNaked | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isNaked method
ms.assetid: b16629dc-8e17-476b-9c7b-58e7277c61ed
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c1bc54c29a94c79be4dafae45128ddb63595f45aec489da7e4e3a0c59a71b45e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121436419"
---
# <a name="idiasymbolget_isnaked"></a>IDiaSymbol::get_isNaked
Recupera un flag che specifica se la funzione ha l'attributo [naked,](/cpp/cpp/naked-cpp) ovvero non ha codice di prologo o epilogo aggiunto dal compilatore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isNaked(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

[out] Restituisce `TRUE` se la funzione ha l'attributo ; in caso `naked` contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Chiamate di funzione Naked](/cpp/cpp/naked-function-calls)
