---
description: Recupera l'ID del registro che include un puntatore di base alle variabili locali nello stack.
title: IDiaSymbol::get_localBasePointerRegisterId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_localBasePointerRegisterId method
ms.assetid: 9cbcaf00-9ace-45e1-b164-7a9439e08083
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 779f88d2199819d9854d9678b9704e90782e3e32
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147296"
---
# <a name="idiasymbolget_localbasepointerregisterid"></a>IDiaSymbol::get_localBasePointerRegisterId
Recupera l'ID del registro che include un puntatore di base alle variabili locali nello stack. Utilizzare quando l' [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) è impostata su `SymTagFunction` .

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_localBasePointerRegisterId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce l'ID del registro che include un puntatore di base alle variabili locali nello stack.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Osservazioni

## <a name="requirements"></a>Requisiti
 Intestazione: dia2. h

 Libreria: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
