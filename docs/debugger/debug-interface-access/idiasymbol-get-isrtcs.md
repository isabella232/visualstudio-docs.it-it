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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: be3833af7ea6dc26e51ef24077f762b3c2a001bc74459820b56f73e868849099
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404714"
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

[out] Puntatore a un oggetto BOOL che specifica se la funzione è stata compilata con stack frame degli errori di run-time.

## <a name="return-value"></a>Valore restituito

 In caso di esito positivo, `S_OK` restituisce ; in caso contrario, restituisce o codice di `S_FALSE` errore.

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
