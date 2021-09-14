---
description: Legge la memoria dall'immagine.
title: IDiaStackWalkFrame::readMemory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: de206ac94a03d6f50d301fed84067e56dbc88a30
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628067"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Legge la memoria dall'immagine.

## <a name="syntax"></a>Sintassi

```C++
HRESULT readMemory ( 
   MemoryTypeEnum type,
   ULONGLONG va,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Parametri
 `type`

[in] Uno dei valori [di enumerazione MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) che specifica il tipo di memoria a cui accedere.

 `va`

[in] Posizione dell'indirizzo virtuale nell'immagine per iniziare la lettura.

 `cbData`

[in] Dimensioni del buffer di dati, in byte.

 `pcbData`

[out] Restituisce il numero di byte restituiti. Se `data` è , contiene il numero totale di byte di dati `NULL` `pcbData` disponibili.

 `data`

[out] Buffer che deve essere compilato con i dati della posizione specificata.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
