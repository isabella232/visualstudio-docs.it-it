---
description: Imposta l'allineamento dell'immagine.
title: IDiaAddressMap::put_imageAlign | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c0817d0b1569557bad7ebc966c1dd23339a134ce
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630539"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
Imposta l'allineamento dell'immagine.

## <a name="syntax"></a>Sintassi

```C++
HRESULT put_imageAlign ( 
   DWORD NewVal
);
```

#### <a name="parameters"></a>Parametri
 NewVal

[in] Nuovo valore di allineamento dell'immagine per l'eseguibile.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Le immagini (file eseguibili caricati) sono allineate ai limiti di memoria specificati. Questo allineamento può essere influenzato dall'architettura di sistema corrente e dalle opzioni della fase di compilazione e di collegamento. L'allineamento delle immagini è sempre ai limiti dei byte. I valori di allineamento delle immagini seguenti sono validi: limiti di 1, 2, 4, 8, 16, 32 e 64 byte.

 L'allineamento dell'immagine corrente può essere recuperato con una chiamata al [metodo IDiaAddressMap::get_imageAlign.](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)

> [!NOTE]
> L'immagine è già caricata nel momento in cui questo metodo può essere chiamato. Il `put_imageAlign` metodo viene in genere usato quando l'immagine è stata spostata o modificata ed è necessario un nuovo allineamento.

## <a name="see-also"></a>Vedi anche
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
