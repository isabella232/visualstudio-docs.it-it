---
title: IDiaSegment::get_frame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_frame method
ms.assetid: 9fece9c7-064a-4d6b-9cef-fc387f322205
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e32f4fddfb7e1fb88bf8b32f27b55305bc913ead
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742428"
---
# <a name="idiasegmentget_frame"></a>IDiaSegment::get_frame
Recupera il numero di segmento.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_frame ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il numero di segmento.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)