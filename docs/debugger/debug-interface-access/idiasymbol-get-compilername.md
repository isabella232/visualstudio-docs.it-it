---
description: Restituisce il nome del compilatore utilizzato per generare il compilazione.
title: IDiaSymbol::get_compilerName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_compilerName method
ms.assetid: 66eaaf72-68d4-40ee-b132-97bea9fe395c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a5360af94cc2c1612b2088dc548216785e1e810a2a9139189fad12d3b5d68e25
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121312036"
---
# <a name="idiasymbolget_compilername"></a>IDiaSymbol::get_compilerName
Restituisce il nome del compilatore utilizzato per generare [compilando](../../debugger/debug-interface-access/compiland.md).

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_compilerName (
   BSTR *pName
);
```

#### <a name="parameters"></a>Parametri
 `pName` Puntatore a un oggetto BSTR che conterrà il nome Unicode del compilatore.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Osservazioni

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
