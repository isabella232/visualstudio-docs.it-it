---
title: IDiaFrameData::get_functionStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 324cad63a597768dc2c13447c6d2d68756878695
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743603"
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

out Restituisce `TRUE` se il blocco contiene il punto di ingresso. in caso contrario, restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 È possibile che un stack frame non sia l'inizio di una funzione perché il frame rappresenta un metodo o una funzione inline inserita in una funzione.

## <a name="see-also"></a>Vedere anche
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)