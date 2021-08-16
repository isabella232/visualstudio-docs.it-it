---
description: Recupera un enumeratore stack frame per le piattaforme x86.
title: IDiaStackWalker::getEnumFrames | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1f450b6717f14776630e354d7f4b7e351a872414c6f1f2076d8ab6ca210d499c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391736"
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
Recupera un enumeratore stack frame per le piattaforme x86.

## <a name="syntax"></a>Sintassi

```C++
HRESULT getEnumFrames( 
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Parametri
 `pHelper`

[in] Oggetto [IDiaStackWalkHelper helper.](../../debugger/debug-interface-access/idiastackwalkhelper.md)

 `ppEnum`

[out] Restituisce un [oggetto IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) che contiene un elenco di [oggetti IDiaStackFrame.](../../debugger/debug-interface-access/idiastackframe.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Per ottenere un stack frame in qualsiasi altra piattaforma, chiamare il metodo [IDiaStackWalker::getEnumFrames2.](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)

## <a name="see-also"></a>Vedi anche
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
