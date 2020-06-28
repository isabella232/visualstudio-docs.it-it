---
title: IDiaImageData::get_imageBase | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00461f73059198f5e9028658100c9ccf400be607
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467176"
---
# <a name="idiaimagedataget_imagebase"></a>IDiaImageData::get_imageBase
Recupera la posizione di memoria in cui deve essere basata l'immagine.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il valore di base dell'immagine suggerito.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 A causa dei conflitti di base dell'immagine, un'immagine potrebbe essere riassegnata automaticamente a una posizione di memoria inutilizzata quando viene caricata. Questo metodo restituisce l'hint di base (posizione di memoria suggerita) archiviato nel modulo in fase di compilazione.

## <a name="see-also"></a>Vedi anche
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)