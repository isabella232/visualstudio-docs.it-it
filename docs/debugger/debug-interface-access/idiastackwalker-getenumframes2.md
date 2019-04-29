---
title: IDiaStackWalker::getEnumFrames2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35886ea0456426c30c44d5fd8e90399d4a2143ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837940"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
Recupera un enumeratore di frame dello stack per un tipo di piattaforma specifica.

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

[in] Un valore compreso il [enumerazione CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) enumerazione che specifica il tipo di piattaforma.

 `pHelper`

[in] L'helper [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) oggetto.

 `ppEnum`

[out] Restituisce un [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) contenente un elenco di oggetti [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) oggetti.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Per ottenere un elenco di frame dello stack per semplicemente x86 piattaforma, chiamare il [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [Enumerazione CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)