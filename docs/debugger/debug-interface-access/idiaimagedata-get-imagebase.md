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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f62e974b6461d3567c67d36bad963c687c3a291
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864922"
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