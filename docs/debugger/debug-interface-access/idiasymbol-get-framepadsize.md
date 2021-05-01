---
description: Recupera le dimensioni aggiuntive del riempimento aggiunte a ogni funzione.
title: IDiaSymbol::get_framePadSize | Microsoft Docs
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePadSize method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d361ec3e144730e49345d3560f815ee5fe0be469
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217232"
---
# <a name="idiasymbolget_framepadsize"></a>IDiaSymbol::get_framePadSize

Recupera le dimensioni aggiuntive del riempimento aggiunte a ogni funzione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_framePadSize ( 
   DWORD* pPadSize
);
```

#### <a name="parameters"></a>Parametri

 `pPadSize`

[out] Restituisce le dimensioni aggiuntive del riempimento aggiunte a ogni funzione.

## <a name="return-value"></a>Valore restituito

 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o il `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti

Le dimensioni aggiuntive del riempimento vengono in genere usate da Modifica e continuazione.

Questo metodo è supportato a partire Visual Studio 2019 versione 16.10 Preview 2.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
