---
description: Recupera un valore che indica se la funzione è stata compilata con il stack frame degli errori di run-time. Si tratta del flag /RTCs.
title: IDiaSymbol::get_isRTCs | Microsoft Docs
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isRTCs method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9a297abe6326af6f04058e6095f59f880f526adb
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217233"
---
# <a name="idiasymbolget_isrtcs"></a>IDiaSymbol::get_isRTCs

Restituisce un valore che indica se la funzione è stata compilata con il stack frame degli errori di run-time. Si tratta del flag /RTCs.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isRTCs ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri

 `pRetVal`

[out] Puntatore a un oggetto BOOL che specifica se la funzione è stata compilata con stack frame degli errori di run-time.

## <a name="return-value"></a>Valore restituito

 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o il `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti

Questo metodo è supportato a partire Visual Studio 2019 versione 16.10 Preview 2.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
