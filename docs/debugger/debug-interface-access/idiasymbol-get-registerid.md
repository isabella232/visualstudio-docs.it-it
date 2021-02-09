---
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
ms.workload:
- multiple
ms.openlocfilehash: d7c63c9464b0d8c716b4946dab5c5b86d198a14c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853674"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
Recupera l'indicatore di registro del percorso quando l' [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) è impostata su `LocIsEnregistered` .

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce l'indicatore di registrazione del percorso.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Se il simbolo è relativo a un registro, ovvero se l' [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) del simbolo è impostata su `LocIsRegRel` , utilizzare il `get_registerId` metodo seguito da una chiamata al metodo [IDiaSymbol:: get_Offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) per ottenere l'offset dal registro in cui si trova il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)