---
description: Recupera l'allineamento dell'immagine corrente.
title: IDiaAddressMap::get_imageAlign | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f8afda829cadbaaea693ebd12b30d6dd3bb7c91c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630551"
---
# <a name="idiaaddressmapget_imagealign"></a>IDiaAddressMap::get_imageAlign
Recupera l'allineamento dell'immagine corrente.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_imageAlign ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il valore di allineamento dell'immagine dal file eseguibile.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Le immagini sono allineate a limiti di memoria specifici a seconda di come l'immagine è stata caricata e creata. L'allineamento è in genere sui limiti di 1, 2, 4, 8, 16, 32 o 64 byte. L'allineamento dell'immagine può essere impostato con una chiamata al metodo [IDiaAddressMap::p ut_imageAlign.](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)

## <a name="see-also"></a>Vedi anche
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)
