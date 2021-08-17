---
description: Restituisce il blocco di dati PDATA associato all'indirizzo virtuale.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c2267173539401f9b673a6cf760abe9070279970
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091149"
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

[in] Specifica l'indirizzo virtuale dei dati da ottenere.

 `cbData`

[in] Dimensioni dei dati in byte da ottenere.

 `pcbData`

[out] Restituisce la dimensione effettiva dei dati in byte ottenuta.

 `pbData`

[in, out] Buffer compilato con i dati richiesti. Non può essere `NULL`.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non esiste alcun PDATA per l'indirizzo specificato. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Il file PDATA (la sezione denominata ".pdata") di un compilando contiene informazioni sulla gestione delle eccezioni per le funzioni.

 Il chiamante sa quanti dati devono essere restituiti in modo che il chiamante non abbia la necessità di chiedere la quantità di dati disponibile. Pertanto, è accettabile che un'implementazione di questo metodo restituirà un errore se il `pbData` parametro è `NULL` .

## <a name="see-also"></a>Vedi anche
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
