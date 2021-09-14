---
description: IDiaFrameData::get_lengthSavedRegisters recupera il numero di byte di registri salvati inseriti nello stack.
title: IDiaFrameData::get_lengthSavedRegisters | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthSavedRegisters method
ms.assetid: dfda4e91-9bfa-4b9d-9133-b73015bfa4d5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: fc5f3ef7a27ef367c1f48bb17bf346322eff6434
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629838"
---
# <a name="idiaframedataget_lengthsavedregisters"></a>IDiaFrameData::get_lengthSavedRegisters
Recupera il numero di byte di registri salvati inseriti nello stack.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_lengthSavedRegisters ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il numero di byte dei registri salvati.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Il valore restituito da questo metodo viene in genere usato nell'interpretazione di una stringa di programma (vedere il metodo [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) per la definizione di una stringa di programma).

## <a name="see-also"></a>Vedi anche
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
