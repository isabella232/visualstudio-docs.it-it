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
ms.openlocfilehash: 5fb7fff92007160abdba64970d652ee73042661b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938133"
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
  
## <a name="remarks"></a>Osservazioni  
 Per ottenere un elenco di frame dello stack per semplicemente x86 piattaforma, chiamare il [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [Enumerazione CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)