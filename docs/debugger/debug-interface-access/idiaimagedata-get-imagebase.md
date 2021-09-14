---
description: Recupera la posizione di memoria in cui deve essere basata l'immagine.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 699ad3a289ff790c414a4c3e8a552436a22ab633
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629784"
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

[out] Restituisce il valore di base dell'immagine suggerita.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 A causa di conflitti di base delle immagini, un'immagine può essere riastratta automaticamente in una posizione di memoria inutilizzata quando viene caricata. Questo metodo restituisce l'hint di base (posizione di memoria suggerita) archiviato nel modulo in fase di compilazione.

## <a name="see-also"></a>Vedi anche
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
