---
description: Ignora un numero specificato di tabelle in una sequenza di enumerazione.
title: IDiaEnumTables::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Skip method
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 54cddc5df34b4aa80dfba71326f61e85a7fab4fa194d7c1fe0a2dee0e93b79f3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345076"
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

[in] Numero di tabelle nella sequenza di enumerazione da ignorare.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce ; in caso contrario, restituisce se `S_OK` non sono presenti altre tabelle da `S_FALSE` ignorare.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
