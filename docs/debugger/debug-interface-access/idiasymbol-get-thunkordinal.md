---
description: Recupera il tipo di thunk di una funzione.
title: IDiaSymbol::get_thunkOrdinal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 06ad9b4e11e81a337095b49a15411688e2974e1f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134139"
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

[out] Restituisce un valore [dall'enumerazione THUNK_ORDINAL Enumeration](../../debugger/debug-interface-access/thunk-ordinal.md) che specifica il tipo di thunk di una funzione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Questa proprietà è valida solo se il simbolo è un [valore di enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) di `SymTagThunk` .

 Un "thunk" è una parte di codice che esegue la conversione tra uno spazio indirizzi di memoria a 32 bit (noto anche come spazio indirizzi flat) e uno spazio indirizzi a 16 bit (noto come spazio indirizzi segmentato).

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
