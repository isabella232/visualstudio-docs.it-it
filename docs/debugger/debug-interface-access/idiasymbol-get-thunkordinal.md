---
title: IDiaSymbol::get_thunkOrdinal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3bc8c523886d694ea413dedcf9a28e53e361882b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739133"
---
# <a name="idiasymbolget_thunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Recupera il tipo di thunk di una funzione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_thunkOrdinal ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce un valore dall'enumerazione Enumerazione [THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) che specifica il tipo di thunk di una funzione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Note
 Questa proprietà è valida solo se il simbolo è un valore di [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) di `SymTagThunk`.

 Un "thunk" è una porzione di codice che esegue la conversione tra uno spazio degli indirizzi di memoria a 32 bit (noto anche come spazio degli indirizzi flat) e uno spazio degli indirizzi a 16 bit (noto come spazio di indirizzi segmentato).

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)