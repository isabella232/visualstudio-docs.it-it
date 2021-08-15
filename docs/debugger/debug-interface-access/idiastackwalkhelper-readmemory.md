---
description: Legge un blocco di dati dall'immagine del file eseguibile in memoria.
title: IDiaStackWalkHelper::readMemory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ce141bcd49bad73daedffa93ec653d53630ea96a2720f4a1daf6e844062712f3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121312076"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Legge un blocco di dati dall'immagine del file eseguibile in memoria.

## <a name="syntax"></a>Sintassi

```C++
HRESULT readMemory( 
   enum MemoryTypeEnum type,
   ULONGLONG           va,
   DWORD               cbData,
   DWORD*              pcbData,
   BYTE*               pbData
);
```

#### <a name="parameters"></a>Parametri
 `type`

[in] Valore [dell'enumerazione MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) che specifica il tipo di memoria da leggere.

 va

[in] Indirizzo virtuale nell'immagine da cui iniziare la lettura.

 `cbData`

[in] Dimensioni del buffer di dati in byte.

 `pcbData`

[out] Restituisce il numero di byte effettivamente letti. Se `pbData` è , questo è il numero totale di byte di dati `NULL` disponibili.

 `pbData`

[in, out] Buffer compilato con la memoria letta.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [Enumerazione MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)
