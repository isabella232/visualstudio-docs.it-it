---
title: IDiaSymbol::get_localBasePointerRegisterId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_localBasePointerRegisterId method
ms.assetid: 9cbcaf00-9ace-45e1-b164-7a9439e08083
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f9ad47a37c2d9306cc4f087719bfef7a52be308
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739881"
---
# <a name="idiasymbolget_localbasepointerregisterid"></a>IDiaSymbol::get_localBasePointerRegisterId
Recupera l'ID del registro che include un puntatore di base alle variabili locali nello stack. Utilizzare quando l' [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) è impostata su `SymTagFunction`.

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
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Note

## <a name="requirements"></a>Requisiti
 Intestazione: dia2. h

 Libreria: diaguids. lib

 DLL: msdia100. dll

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)