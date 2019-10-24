---
title: IDiaAddressMap::put_imageAlign | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b1a6bf037dc87d84fab21622571158fb0682f60
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745058"
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

in Nuovo valore di allineamento dell'immagine per l'eseguibile.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Le immagini (file eseguibili caricati) sono allineate ai limiti di memoria specificati. Questo allineamento può essere influenzato dall'architettura del sistema corrente e dalle opzioni di tempo di compilazione e collegamento. L'allineamento delle immagini è sempre in corrispondenza dei limiti di byte. I valori di allineamento immagine seguenti sono validi: 1, 2, 4, 8, 16, 32 e 64 limiti di byte.

 L'allineamento dell'immagine corrente può essere recuperato con una chiamata al metodo [IDiaAddressMap:: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) .

> [!NOTE]
> L'immagine è già caricata nel momento in cui è possibile chiamare questo metodo. Il metodo `put_imageAlign` viene in genere usato quando l'immagine è stata spostata o modificata ed è necessario un nuovo allineamento.

## <a name="see-also"></a>Vedere anche
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)