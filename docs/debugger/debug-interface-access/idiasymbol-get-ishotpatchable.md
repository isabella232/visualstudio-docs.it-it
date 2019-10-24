---
title: IDiaSymbol::get_isHotpatchable | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isHotpatchable method
ms.assetid: b7b6f490-1cf2-4a68-9237-b152dac84d3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27218a2814e14e0a1ec30bd7fb4dc4840589251c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740224"
---
# <a name="idiasymbolget_ishotpatchable"></a>IDiaSymbol::get_isHotpatchable
Recupera un flag che indica se il modulo è stato compilato con l'opzione del compilatore [/hotpatch (Create Hotpatchable Image)](/cpp/build/reference/hotpatch-create-hotpatchable-image) .

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isHotpatchable(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

out Restituisce `TRUE` se il modulo è con patch a caldo; in caso contrario, restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Note
 Questa proprietà è disponibile dal tipo di simbolo `SymTagCompilandDetails` (vedere [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)).

## <a name="requirements"></a>Requisiti

|Requisiti|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)