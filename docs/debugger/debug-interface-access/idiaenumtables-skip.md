---
title: 'IDiaEnumTables:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Skip method
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27daf70a3cc5f155bfbe6b2678cce42b50801153
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467463"
---
# <a name="idiaenumtablesskip"></a>IDiaEnumTables::Skip
Ignora un numero specificato di tabelle in una sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametri
 `celt`

in Numero di tabelle nella sequenza di enumerazione da ignorare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` se non sono presenti altre tabelle da ignorare.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)