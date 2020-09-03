---
title: IDiaSymbol::get_compilerGenerated | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_compilerGenerated method
ms.assetid: 864d9249-f0c8-4a34-b391-eb785f7e8865
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29d7255fd0e2c769a1b7d318e56982ba739915d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464086"
---
# <a name="idiasymbolget_compilergenerated"></a>IDiaSymbol::get_compilerGenerated
Recupera un flag che indica se il simbolo è stato generato dal compilatore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_compilerGenerated ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce `TRUE` se il compilatore ha generato il simbolo; in caso contrario, restituisce `FALSE` se il simbolo è stato generato dall'origine scritta dall'utente.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)