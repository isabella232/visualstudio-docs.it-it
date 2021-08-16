---
description: Restituisce un indicatore di una convenzione di chiamata dei metodi.
title: IDiaSymbol::get_callingConvention | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_callingConvention method
ms.assetid: 355d3877-b6b6-45fd-a1d8-baed428d8f96
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b9e4f010bede2e3c51369f4a31a30f6a1d18660ff30f7f867eee63cc2583c42d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420790"
---
# <a name="idiasymbolget_callingconvention"></a>IDiaSymbol::get_callingConvention
Restituisce un indicatore di una convenzione di chiamata dei metodi.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_callingConvention ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce un valore [dall'enumerazione CV_call_e enumeration](../../debugger/debug-interface-access/cv-call-e.md) che specifica la convenzione di chiamata di un metodo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione CV_call_e](../../debugger/debug-interface-access/cv-call-e.md)
