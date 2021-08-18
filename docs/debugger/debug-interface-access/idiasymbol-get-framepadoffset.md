---
description: Recupera l'offset del riquadro dello stack dal registro del puntatore ai frame.
title: IDiaSymbol::get_framePadOffset | Microsoft Docs
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePadOffset method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2bccd0087c22072efd016fe43646cceb75cf8a18
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044246"
---
# <a name="idiasymbolget_framepadoffset"></a>IDiaSymbol::get_framePadOffset

Recupera l'offset del riquadro dello stack dal registro del puntatore ai frame.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_framePadOffset ( 
   DWORD* pPadOffset
);
```

#### <a name="parameters"></a>Parametri

 `pPadOffset`

[out] Restituisce l'offset del blocco stack.

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
