---
title: IDiaSegment::get_addressSection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_addressSection method
ms.assetid: 360b61b1-69b1-4a8b-ba37-97a1d835ac53
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e098f1e2367395f201abf6f44554f1699400b12
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635722"
---
# <a name="idiasegmentgetaddresssection"></a>IDiaSegment::get_addressSection
Recupera il numero di sezione che viene eseguito il mapping a questo segmento.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il numero di sezione che viene eseguito il mapping a questo segmento.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)