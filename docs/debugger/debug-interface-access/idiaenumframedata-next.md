---
description: Recupera un numero specificato di elementi dati del frame nella sequenza di enumerazione.
title: IDiaEnumFrameData::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 57324a0ec9b82ff0b32f16ebf32f8d3ee9e19fb5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134609"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
Recupera un numero specificato di elementi dati del frame nella sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Next ( 
   ULONG           celt,
   IDiaFrameData** rgelt,
   ULONG*          pceltFetched
);
```

#### <a name="parameters"></a>Parametri
 celt

[in] Numero di elementi dati del frame nell'enumeratore da recuperare.

 Rgelt

[out] Matrice di oggetti [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) da riempire con gli elementi dati del frame richiesti.

 pceltFetched

[out] Restituisce il numero di elementi dati del frame nell'enumeratore recuperato.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti altri record. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
