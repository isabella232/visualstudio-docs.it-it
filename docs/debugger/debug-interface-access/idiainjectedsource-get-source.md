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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: bd210d3d4130d94193abec38c41bda7bce67eaaa
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629747"
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

[in] Numero di byte che rappresenta le dimensioni del buffer di dati.

 `pcbData`

[out] Restituisce il numero di byte che rappresenta i byte restituiti. Se `data` è , è il numero totale di byte di dati `NULL` `pcbData` disponibili.

 `data[]`

[out] Buffer da riempire con i byte di origine.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
