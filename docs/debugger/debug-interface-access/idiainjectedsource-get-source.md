---
description: Recupera i byte del codice sorgente.
title: IDiaInjectedSource::get_source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 248fc00320f94b297a9b0697742dff6e3fbd2004
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148416"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
Recupera i byte del codice sorgente.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_source ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametri
 `cbData`

in Numero di byte che rappresenta la dimensione del buffer di dati.

 `pcbData`

out Restituisce il numero di byte che rappresenta i byte restituiti. Se `data` è `NULL` , `pcbData` è il numero totale di byte dei dati disponibili.

 `data[]`

out Buffer da compilare con i byte di origine.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
