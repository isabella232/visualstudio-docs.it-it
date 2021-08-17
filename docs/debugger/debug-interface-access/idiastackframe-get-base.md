---
description: Recupera l'indirizzo di base del frame.
title: IDiaStackFrame::get_base | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_base method
ms.assetid: f27477d7-26fe-4c1c-a08a-c52cb20c8293
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0513272e6dfaca63b9656952cc2880bf943e91da
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128895"
---
# <a name="idiastackframeget_base"></a>IDiaStackFrame::get_base
Recupera l'indirizzo di base del frame.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_base ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce l'indirizzo di base.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se la proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
