---
title: IDiaStackFrame::get_functionStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_functionStart
ms.assetid: e3e6e88b-0594-4d82-9457-480239a2e85a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9900b6301388479fc71f1b257113974056aeb3b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741729"
---
# <a name="idiastackframeget_functionstart"></a>IDiaStackFrame::get_functionStart
Recupera un flag che indica se il blocco contiene il punto di ingresso di una funzione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_functionStart ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce `TRUE` se il stack frame contiene il punto di ingresso di una funzione. in caso contrario, restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se la proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)