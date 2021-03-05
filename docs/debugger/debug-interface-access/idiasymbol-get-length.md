---
description: Recupera il numero di bit o byte di memoria utilizzati dall'oggetto rappresentato da questo simbolo.
title: IDiaSymbol::get_length | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_length method
ms.assetid: cc62f028-d195-4fbf-93bc-10b08bef52d2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9a7b3a7a88c688f8ff68f2c1280390f10110c3a9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162012"
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
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Se l' [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) del simbolo è `LocIsBitField` , la lunghezza restituita da questo metodo è in bit. in caso contrario, la lunghezza è in byte per tutti gli altri tipi di posizione.

## <a name="example"></a>Esempio

```C++
IDiaSymbol* pSymbol;
ULONGLONG   length;
pSymbol->get_length( &length );
```

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)
