---
title: IDiaImageData::get_imageBase | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 7887fea30b04f4ebb6605169c58551122eccf73d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743444"
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
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 A causa dei conflitti di base dell'immagine, un'immagine potrebbe essere riassegnata automaticamente a una posizione di memoria inutilizzata quando viene caricata. Questo metodo restituisce l'hint di base (posizione di memoria suggerita) archiviato nel modulo in fase di compilazione.

## <a name="see-also"></a>Vedere anche
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)