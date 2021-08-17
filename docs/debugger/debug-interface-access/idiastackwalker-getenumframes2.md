---
description: Recupera un enumeratore stack frame per un tipo di piattaforma specifico.
title: IDiaStackWalker::getEnumFrames2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 06c5017323b1ad9d139d8a0b2fd4296a2def356cee983216006471c071956b50
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454849"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
Recupera un enumeratore stack frame per un tipo di piattaforma specifico.

## <a name="syntax"></a>Sintassi

```C++

      HRESULT getEnumFrames2( 
   enum  CV_CPU_TYPE_e    cpuid,
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Parametri
 `cpuid`

[in] Valore [dell'enumerazione CV_CPU_TYPE_e,](../../debugger/debug-interface-access/cv-cpu-type-e.md) che specifica il tipo di piattaforma.

 `pHelper`

[in] Oggetto [IDiaStackWalkHelper helper.](../../debugger/debug-interface-access/idiastackwalkhelper.md)

 `ppEnum`

[out] Restituisce un [oggetto IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) contenente un elenco di [oggetti IDiaStackFrame.](../../debugger/debug-interface-access/idiastackframe.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Per ottenere un stack frame solo per la piattaforma x86, chiamare il metodo [IDiaStackWalker::getEnumFrames.](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)

## <a name="see-also"></a>Vedi anche
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [Enumerazione CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
