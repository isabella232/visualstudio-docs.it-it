---
title: IDiaSymbol::get_customCallingConvention | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_customCallingConvention method
ms.assetid: 0aa97951-f7e1-4fa5-a87f-2920460c122d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01fb33108c9952b8543d36b64b7743f4c0531be5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740742"
---
# <a name="idiasymbolget_customcallingconvention"></a>IDiaSymbol::get_customCallingConvention
Recupera un flag che specifica se la funzione dispone di una convenzione di chiamata personalizzata.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_customCallingConvention(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

out Restituisce `TRUE` se la funzione dispone di una convenzione di chiamata personalizzata. in caso contrario, restituisce `FALSE`, la funzione dispone di una convenzione di chiamata nota.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisiti|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)