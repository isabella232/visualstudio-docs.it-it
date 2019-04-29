---
title: IDiaStackFrame::get_systemExceptionHandling | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_systemExceptionHandling
ms.assetid: c76cf265-dea0-4159-883f-32b50bbef044
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 519602b09ea1adcf00ed534ecb22b4a082018464
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838041"
---
# <a name="idiastackframegetsystemexceptionhandling"></a>IDiaStackFrame::get_systemExceptionHandling
Recupera un flag che indica se la gestione delle eccezioni di sistema è in vigore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_systemExceptionHandling ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se la gestione delle eccezioni di sistema è attivo per questo frame; in caso contrario, restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se la proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 La gestione delle eccezioni di sistema è noto anche come gestione strutturata delle eccezioni. Questo non è la stessa operazione come la gestione delle eccezioni C++.

 Per determinare se C++ gestione delle eccezioni è attivo, chiamare il [Get_cplusplusexceptionhandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md) metodo.

## <a name="see-also"></a>Vedere anche
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)