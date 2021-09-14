---
description: Recupera il valore di un registro specificato come archiviato nel stack frame.
title: IDiaStackFrame::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e58f03a45b1fe680644c1bbc320383d6e3ac44ef
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628949"
---
# <a name="idiastackframeget_registervalue"></a>IDiaStackFrame::get_registerValue
Recupera il valore di un registro specificato come archiviato nel stack frame.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_registerValue(
   ULONG      registerIndex,
   ULONGLONG *pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `registerIndex`

[in] Uno dei valori di [enumerazione CV_HREG_e enumeration.](../../debugger/debug-interface-access/cv-hreg-e.md)

 `pRetVal`

[out] Valore archiviato nel registro.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [Enumerazione CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)
