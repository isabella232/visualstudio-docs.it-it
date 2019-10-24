---
title: IDiaSymbol::get_length | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_length method
ms.assetid: cc62f028-d195-4fbf-93bc-10b08bef52d2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 114d9f7b00bbe5d322e7b6893e96fbbabec9d002
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739987"
---
# <a name="idiasymbolget_length"></a>IDiaSymbol::get_length
Recupera il numero di bit o byte di memoria utilizzati dall'oggetto rappresentato da questo simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_length ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il numero di byte o bit di memoria utilizzati dall'oggetto rappresentato da questo simbolo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Note
 Se l' [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) del simbolo è `LocIsBitField`, la lunghezza restituita da questo metodo è in bit; in caso contrario, la lunghezza è in byte per tutti gli altri tipi di località.

## <a name="example"></a>Esempio

```C++
IDiaSymbol* pSymbol;
ULONGLONG   length;
pSymbol->get_length( &length );
```

## <a name="requirements"></a>Requisiti

|Requisiti|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)