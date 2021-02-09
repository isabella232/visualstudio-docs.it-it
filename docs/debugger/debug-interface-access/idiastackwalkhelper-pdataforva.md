---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d150e777f657fcf63dc66dbe3e686c1b445dd473
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863809"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Restituisce il blocco di dati PDATA associato all'indirizzo virtuale.

## <a name="syntax"></a>Sintassi

```C++
HRESULT pdataForVA( 
   ULONGLONG  va,
   DWORD      cbData,
   DWORD*     pcbData,
   BYTE*      pbData
);
```

#### <a name="parameters"></a>Parametri
 `va`

in Specifica l'indirizzo virtuale dei dati da ottenere.

 `cbData`

in Dimensioni dei dati in byte da ottenere.

 `pcbData`

out Restituisce le dimensioni effettive dei dati in byte ottenuti.

 `pbData`

[in, out] Buffer compilato con i dati richiesti. Non può essere `NULL`.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non è presente pData per l'indirizzo specificato. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 PDATA (la sezione denominata ". pData") di un modulo contiene informazioni sulla gestione delle eccezioni per le funzioni.

 Il chiamante sa la quantità di dati da restituire, in modo che il chiamante non debba richiedere la quantità di dati disponibili. Pertanto, è accettabile che un'implementazione di questo metodo restituisca un errore se il `pbData` parametro è `NULL` .

## <a name="see-also"></a>Vedi anche
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)