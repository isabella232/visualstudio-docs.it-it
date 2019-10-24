---
title: 'IDiaStackWalkHelper:: imageForVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 609a9370181937323f2bc3e8ca0a0765cd1f4a12
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741391"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Restituisce l'inizio dell'immagine di un eseguibile in memoria, dato un indirizzo virtuale in un punto qualsiasi dello spazio di memoria dell'eseguibile.

## <a name="syntax"></a>Sintassi

```C++
HRESULT imageForVA(
   ULONGLONG  vaContext,
   ULONGLONG *pvaImageStart
);
```

#### <a name="parameters"></a>Parametri
 `vaContext`

in Indirizzo virtuale situato in un punto qualsiasi dello spazio dell'eseguibile.

 `pvaImageStart`

out Restituisce l'indirizzo virtuale iniziale dell'immagine dell'eseguibile.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)