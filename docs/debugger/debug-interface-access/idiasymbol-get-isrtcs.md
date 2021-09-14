---
description: Recupera un valore che indica se la funzione è stata compilata con stack frame controllo degli errori di run-time. Si tratta del flag /RTCs.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 47f4ad2d6ac2265052d48af2c33471d9c03ae912
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709963"
---
# <a name="idiasymbolget_isrtcs"></a>IDiaSymbol::get_isRTCs

Restituisce un valore che indica se la funzione è stata compilata con stack frame controllo degli errori di run-time. Si tratta del flag /RTCs.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isRTCs ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri

 `pRetVal`

[out] Puntatore a un oggetto BOOL che specifica se la funzione è stata compilata con stack frame controllo degli errori di run-time.

## <a name="return-value"></a>Valore restituito

 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o codice `S_FALSE` di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti

Questo metodo è supportato a partire da Visual Studio 2019 versione 16.10 Preview 2.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
