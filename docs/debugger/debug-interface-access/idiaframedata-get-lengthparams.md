---
description: IDiaFrameData::get_lengthParams recupera il numero di byte di parametri inseriti nello stack.
title: IDiaFrameData::get_lengthParams | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthParams method
ms.assetid: a9177ed6-9ba8-4384-b411-24cad07d031b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1e2ba52cfedbb109d3ebc1d2c3bf1b6704d46f8a2ef0ac496104bd1054b6145d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121326073"
---
# <a name="idiaframedataget_lengthparams"></a>IDiaFrameData::get_lengthParams
Recupera il numero di byte dei parametri inseriti nello stack.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_lengthParams ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il numero di byte dei parametri.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Il valore restituito da questo metodo viene in genere usato nell'interpretazione di una stringa di programma (vedere il metodo [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) per la definizione di una stringa di programma).

## <a name="see-also"></a>Vedi anche
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
