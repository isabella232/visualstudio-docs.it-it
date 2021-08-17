---
description: Recupera le dimensioni del stack frame in byte.
title: IDiaStackFrame::get_size | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_size method
ms.assetid: 71e2f5ab-4aa8-4922-aa8a-b7db97ee143c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 91a3e7af8dda3c18395e5afdb15419a29728a910
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128831"
---
# <a name="idiastackframeget_size"></a>IDiaStackFrame::get_size
Recupera le dimensioni del stack frame in byte.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_size ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce le dimensioni del stack frame in byte.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se la proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
