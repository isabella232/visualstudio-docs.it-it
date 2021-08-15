---
description: Recupera l'elemento di designazione del registro della posizione quando l'enumerazione LocationType è impostata su LocIsEnregistered'.
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
ms.openlocfilehash: 2a82c9b0cc7c2db8ad7b0bc5329ab74fb7f4ef1e274c5366e71afd3ff665ce1d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240464"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
Recupera l'elemento di designazione del registro della posizione quando [l'enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) è impostata su `LocIsEnregistered` .

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce l'elemento di designazione del registro della posizione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Se il simbolo è relativo a un registro, ad esempio se l'enumerazione [LocationType](../../debugger/debug-interface-access/locationtype.md) del simbolo è impostata su , usare il metodo seguito da una chiamata al metodo `LocIsRegRel` `get_registerId` [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) per ottenere l'offset dal registro in cui si trova il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)
