---
title: IDiaEnumStackFrames::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffde40e221823d9656c4b6414b14067ac9d0537a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744033"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Recupera un numero specificato di elementi stack frame dalla sequenza di enumerazione.

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

in Numero di elementi StackFrame nell'enumeratore da recuperare.

 rgelt

out Matrice che deve essere compilata con gli oggetti [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) richiesti.

 pceltFetched

out Restituisce il numero di elementi stack frame nell'enumeratore recuperato.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti altri stack frame. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)