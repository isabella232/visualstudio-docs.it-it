---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f682f3fe0e300f84dc28b959497138a5019f954b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464828"
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

in Uno dei valori di enumerazione dell' [enumerazione MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) che specifica il tipo di memoria a cui accedere.

 `va`

in Posizione dell'indirizzo virtuale nell'immagine da cui iniziare la lettura.

 `cbData`

in Dimensioni in byte del buffer di dati.

 `pcbData`

out Restituisce il numero di byte restituiti. Se `data` è `NULL` , `pcbData` contiene il numero totale di byte dei dati disponibili.

 `data`

out Buffer da compilare con i dati del percorso specificato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)