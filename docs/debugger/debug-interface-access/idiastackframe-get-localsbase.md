---
title: IDiaStackFrame::get_localsBase | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_localsBase method
ms.assetid: eb0bd73e-d92d-468e-a0b1-fbc279919f54
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ae3f83469e14e826802ca82d3d58686a340d9e0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741653"
---
# <a name="idiastackframeget_localsbase"></a>IDiaStackFrame::get_localsBase
Recupera l'indirizzo di base delle variabili locali per il frame.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_localsBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce l'indirizzo di base delle variabili locali.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se la proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)