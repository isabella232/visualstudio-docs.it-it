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
ms.openlocfilehash: 2126d59d223e4923609071fa130b1cac465073ad
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616950"
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
Imposta l'allineamento dell'immagine.

## <a name="syntax"></a>Sintassi

```C++
HRESULT put_imageAlign ( 
   DWORD NewVal
);
```

#### <a name="parameters"></a>Parametri
 NewVal

[in] Il valore di allineamento immagine nuova del file eseguibile.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Immagini (caricare file eseguibili) sono allineate a limiti di memoria specificato. Questo allineamento può essere influenzato dall'architettura di sistema corrente e da opzioni della fase di compilazione e collegamento. Allineamento dell'immagine è sempre nei limiti di byte. I valori di allineamento di immagine seguenti sono validi: i limiti di 1, 2, 4, 8, 16, 32 e 64 byte.

 L'allineamento dell'immagine corrente può essere recuperato con una chiamata per il [Get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) (metodo).

> [!NOTE]
>  L'immagine è già caricata entro l'ora di che questo metodo può essere chiamato. Il `put_imageAlign` metodo viene in genere utilizzato quando l'immagine è stato spostato o modificato e un allineamento nuovo è obbligatorio.

## <a name="see-also"></a>Vedere anche
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)