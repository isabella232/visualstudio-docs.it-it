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
ms.openlocfilehash: 6dadfff62502af59652e9113553e13b4942c540f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63401337"
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Recupera il tipo di thunk di una funzione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_thunkOrdinal ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce un valore compreso il [enumerazione THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) enumerazione che specifica il tipo di thunk di una funzione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Note
 Questa proprietà è valida solo se il simbolo come un [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) pari a `SymTagThunk`.

 Un "thunk" è un frammento di codice che esegue la conversione tra uno spazio di indirizzi di memoria a 32 bit (noto anche come spazio di indirizzi flat) e uno spazio di indirizzi di 16 bit (noto come uno spazio degli indirizzi segmentati).

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)