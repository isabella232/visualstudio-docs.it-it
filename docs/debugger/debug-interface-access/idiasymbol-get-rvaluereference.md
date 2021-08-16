---
description: Recupera un flag che specifica se un tipo di puntatore è un riferimento rvalue.
title: IDiaSymbol::get_RValueReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_RValueReference method
ms.assetid: c6c8c543-253e-4c23-a939-3e66f3db0ee2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 700754cad6329d16aba5e47b998a4da7810e8444d94532ce0f0ab4e1685d4cbe
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121264114"
---
# <a name="idiasymbolget_rvaluereference"></a>IDiaSymbol::get_RValueReference
Recupera un flag che specifica se un tipo di puntatore è un riferimento rvalue. Utilizzare quando [l'enumerazione SymTagEnum è](../../debugger/debug-interface-access/symtagenum.md) impostata su un tipo di puntatore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_RValueReference (
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se il puntatore è un riferimento rvalue; in caso contrario, restituisce `FALSE` .

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
