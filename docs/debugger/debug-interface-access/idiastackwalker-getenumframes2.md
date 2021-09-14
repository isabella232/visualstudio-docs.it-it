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
ms.openlocfilehash: 80fbd406a9ad2d3aa691e1fd2650222447d0e109
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635403"
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

[in] Valore dell'enumerazione [CV_CPU_TYPE_e,](../../debugger/debug-interface-access/cv-cpu-type-e.md) che specifica il tipo di piattaforma.

 `pHelper`

[in] Oggetto [IDiaStackWalkHelper dell'helper.](../../debugger/debug-interface-access/idiastackwalkhelper.md)

 `ppEnum`

[out] Restituisce un [oggetto IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) contenente un elenco [di oggetti IDiaStackFrame.](../../debugger/debug-interface-access/idiastackframe.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Per ottenere un stack frame solo per la piattaforma x86, chiamare il [metodo IDiaStackWalker::getEnumFrames.](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)

## <a name="see-also"></a>Vedi anche
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [Enumerazione CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
