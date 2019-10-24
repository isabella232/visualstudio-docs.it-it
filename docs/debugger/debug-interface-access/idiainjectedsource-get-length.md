---
title: IDiaInjectedSource::get_length | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_length method
ms.assetid: 38b88b8b-c2e0-4b2d-8b8b-9ff373733e78
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95c51910ee638338f588b1e81b844cf3f487a50e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743359"
---
# <a name="idiainjectedsourceget_length"></a>IDiaInjectedSource::get_length
Recupera il numero di byte di codice.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_length ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il numero di byte di codice.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Il valore restituito da questo metodo è la lunghezza del codice sorgente ed è lo stesso valore restituito dal metodo [IDiaInjectedSource:: get_Source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md) .

## <a name="see-also"></a>Vedere anche
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
- [IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)