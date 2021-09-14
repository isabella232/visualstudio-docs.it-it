---
description: Recupera un numero specificato di stack frame elementi dalla sequenza di enumerazione.
title: IDiaEnumStackFrames::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 76248ef1feb330157895ccd24d8fa071b3e857bd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630059"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Recupera un numero specificato di stack frame elementi dalla sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>Parametri
 celt

[in] Numero di elementi dello stackframe nell'enumeratore da recuperare.

 Rgelt

[out] Matrice che deve essere compilata con gli oggetti [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) richiesti.

 pceltFetched

[out] Restituisce il numero di stack frame nell'enumeratore recuperato.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti altri stack frame. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
