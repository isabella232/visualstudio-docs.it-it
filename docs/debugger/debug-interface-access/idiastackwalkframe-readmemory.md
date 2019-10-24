---
title: IDiaStackWalkFrame::readMemory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: ae1201fca1fc25cce19b40b47d6435d02d80e1b4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741472"
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

out Restituisce il numero di byte restituiti. Se `data` è `NULL`, `pcbData` contiene il numero totale di byte di dati disponibili.

 `data`

out Buffer da compilare con i dati del percorso specificato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)