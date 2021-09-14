---
description: IDiaStackFrame::get_lengthParams recupera il numero di byte di parametri inseriti nello stack.
title: IDiaStackFrame::get_lengthParams | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthParams method
ms.assetid: 78005efa-2883-4823-b4e4-711a66672c78
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 36aca2df154f70902f65fa4bee9546d14f4bad94
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628991"
---
# <a name="idiastackframeget_lengthparams"></a>IDiaStackFrame::get_lengthParams
Recupera il numero di byte di parametri inseriti nello stack.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_lengthParams ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il numero di byte di parametri.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se la proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
