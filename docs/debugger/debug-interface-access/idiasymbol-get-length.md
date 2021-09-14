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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a02dc44d8ac2af51a1feb2791ef289cb0a7ff7aa
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709944"
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

[out] Restituisce il numero di byte o bit di memoria utilizzato dall'oggetto rappresentato da questo simbolo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Se [l'enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) del simbolo è , la lunghezza restituita da questo metodo è in bit; in caso contrario, la lunghezza è in byte per tutti gli `LocIsBitField` altri tipi di posizione.

## <a name="example"></a>Esempio

```C++
IDiaSymbol* pSymbol;
ULONGLONG   length;
pSymbol->get_length( &length );
```

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)
