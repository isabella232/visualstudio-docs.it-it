---
title: IDiaInjectedSource::get_source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b389df8220766ffbdbf865a2b8e70877fe91b3f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743341"
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

out Restituisce il numero di byte che rappresenta i byte restituiti. Se `data` è `NULL`, `pcbData` è il numero totale di byte di dati disponibili.

 `data[]`

out Buffer da compilare con i byte di origine.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)