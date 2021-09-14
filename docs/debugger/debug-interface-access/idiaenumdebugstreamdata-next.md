---
description: Recupera un numero specificato di record nella sequenza enumerata.
title: IDiaEnumDebugStreamData::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8b67d12b983ef13ad92ee8a121d8733d435f7b7c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630426"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
Recupera un numero specificato di record nella sequenza enumerata.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Next ( 
   ULONG  celt,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[],
   ULONG* pceltFetched
);
```

#### <a name="parameters"></a>Parametri
 celt

[in] Numero di record da recuperare.

 cbData

[in] Dimensioni del buffer di dati, in byte.

 pcbData

[out] Restituisce il numero di byte restituiti. Se `data` è NULL, contiene `pcbData` il numero totale di byte di dati disponibili per tutti i record richiesti.

 data[]

[out] Buffer da riempire con i dati del record del flusso di debug.

 pceltFetched

[in, out] Restituisce il numero di record in `data` .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti altri record. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)
