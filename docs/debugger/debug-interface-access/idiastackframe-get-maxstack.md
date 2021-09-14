---
description: IDiaStackFrame::get_maxStack recupera il numero massimo di byte inseriti nello stack nel frame.
title: IDiaStackFrame::get_maxStack | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_maxStack method
ms.assetid: 6352e972-7105-4d0e-aeba-b8fc16d62dec
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4ec5aab1561d70488a8e57db85a74fdca9da70cd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628956"
---
# <a name="idiastackframeget_maxstack"></a>IDiaStackFrame::get_maxStack
Recupera il numero massimo di byte inseriti nello stack nel frame.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_maxStack ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il numero massimo di byte inseriti nello stack.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se la proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
