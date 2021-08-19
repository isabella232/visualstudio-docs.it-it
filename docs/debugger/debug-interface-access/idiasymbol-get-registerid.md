---
description: Recupera l'oggetto register designator della posizione quando l'enumerazione LocationType) è impostata su LocIsEnregistered'.
title: IDiaSymbol::get_registerId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 715fc20baafeaf6ed7adb8790b84daedfc9d3b19
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147232"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
Recupera l'designatore del registro della posizione quando [l'enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) è impostata su `LocIsEnregistered` .

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce l'designatore del registro della posizione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Se il simbolo è relativo a un registro, ad esempio se l'enumerazione [LocationType](../../debugger/debug-interface-access/locationtype.md) del simbolo è impostata su , usare il metodo seguito da una chiamata al metodo `LocIsRegRel` `get_registerId` [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) per ottenere l'offset dal registro in cui si trova il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)
