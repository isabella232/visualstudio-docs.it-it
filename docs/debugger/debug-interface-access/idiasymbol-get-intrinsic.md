---
description: Recupera un flag che specifica se una classe è un tipo intrinseco.
title: IDiaSymbol::get_intrinsic | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intrinsic method
ms.assetid: f969f595-d9f9-48b9-adaa-63a6e4e09575
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4e5ac1796a1a876a454dc976688799ba1033570e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052245"
---
# <a name="idiasymbolget_intrinsic"></a>IDiaSymbol::get_intrinsic
Recupera un flag che specifica se una classe è un tipo intrinseco.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_intrinsic( 
   BOOL* pRetVal)
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se la classe è un tipo intrinseco; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Osservazioni

## <a name="requirements"></a>Requisiti
 Intestazione: Dia2.h

 Libreria: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
