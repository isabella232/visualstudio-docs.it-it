---
description: Recupera un controllo di ridondanza ciclico (CRC) calcolato dai byte del codice sorgente.
title: IDiaInjectedSource::get_crc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_crc method
ms.assetid: 2ecdda93-950e-40d6-b79b-4ae3c55b6cfc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 396a0742b2ac2c3afd8d2868326a701f6f0da6d5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629760"
---
# <a name="idiainjectedsourceget_crc"></a>IDiaInjectedSource::get_crc
Recupera un controllo di ridondanza ciclico (CRC) calcolato dai byte del codice sorgente.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_crc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il CRC calcolato dai byte del codice sorgente.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
