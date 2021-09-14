---
description: IDiaFrameData::get_functionStart recupera un flag che indica se il blocco contiene il punto di ingresso di una funzione.
title: IDiaFrameData::get_functionStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b33b08a00d62c89228346e5171219a801b0ad2a9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629873"
---
# <a name="idiaframedataget_functionstart"></a>IDiaFrameData::get_functionStart
Recupera un flag che indica se il blocco contiene il punto di ingresso di una funzione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_functionStart ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se il blocco contiene il punto di ingresso; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 È possibile che un stack frame non sia l'inizio di una funzione perché il frame rappresenta un metodo o una funzione inline inserita in una funzione.

## <a name="see-also"></a>Vedi anche
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
