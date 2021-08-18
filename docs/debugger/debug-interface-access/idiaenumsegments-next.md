---
description: Recupera un numero specificato di segmenti nella sequenza di enumerazione.
title: IDiaEnumSegments::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5aaed8e83a49ab31844d7fddd5f8e036fdc0d6cd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036399"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Recupera un numero specificato di segmenti nella sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Next ( 
   ULONG         celt,
   IDiaSegment** rgelt,
   ULONG*        pceltFetched
);
```

#### <a name="parameters"></a>Parametri
 celt

[in] Numero di segmenti nell'enumeratore da recuperare.

 Rgelt

[out] Matrice che deve essere compilata con gli oggetti [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) desiderati che rappresentano i segmenti.

 pceltFetched

[out] Restituisce il numero di segmenti nell'enumeratore recuperato.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti altri segmenti. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
