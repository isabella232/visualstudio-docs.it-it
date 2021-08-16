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
ms.openlocfilehash: 5a4ec2e800a0c5eac80832a1b878d2f63d1251e2b6f0e576fd750f3d1e5111de
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380506"
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
