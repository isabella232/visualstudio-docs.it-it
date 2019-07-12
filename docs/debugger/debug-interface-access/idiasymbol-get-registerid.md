---
title: IDiaSymbol::get_registerId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e2b1cbb6837ca139e735bef17bc0c2712d9cae7
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "64786581"
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
Recupera l'identificatore di registro del percorso quando la [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) è impostata su `LocIsEnregistered`.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce l'identificatore di registro della posizione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Note
 Se il simbolo è relativo a un registro, vale a dire, se il simbolo [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md) è impostata su `LocIsRegRel`, usare i `get_registerId` metodo seguita da una chiamata al [Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) metodo per ottenere l'offset dal registro in cui si trova il simbolo.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)