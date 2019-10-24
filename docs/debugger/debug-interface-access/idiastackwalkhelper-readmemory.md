---
title: IDiaStackWalkHelper::readMemory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57afd033b2d969a4ed57dc713b2c4266e0ead632
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741358"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Legge un blocco di dati dall'immagine dell'eseguibile in memoria.

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

in Valore dell'enumerazione di [enumerazione MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) che specifica il tipo di memoria da leggere.

 va

in Indirizzo virtuale nell'immagine da cui iniziare la lettura.

 `cbData`

in Dimensioni in byte del buffer di dati.

 `pcbData`

out Restituisce il numero di byte effettivamente letti. Se `pbData` è `NULL`, indica il numero totale di byte di dati disponibili.

 `pbData`

[in, out] Buffer compilato con la memoria letta.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [Enumerazione MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)