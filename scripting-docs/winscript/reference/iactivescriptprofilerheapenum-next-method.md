---
title: 'Metodo iactivescriptprofilerheapenum:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0336286f-1dcd-4df9-adf5-76b59b4e74bb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4bad607db168d5f3e3533087c94c6c0970f5eb24
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157607"
---
# <a name="iactivescriptprofilerheapenumnext-method"></a>Metodo IActiveScriptProfilerHeapEnum::Next
Ottiene gli oggetti successivo nel set di oggetti degli heap dal [metodo IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Next (    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] PROFILER_HEAP_OBJECT** heapObjects,     [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 Il numero di oggetti da restituire.  
  
 `heapObjects`  
 [out] La prossima [struttura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) strutture.  
  
 `pceltFetched`  
 [out] Il numero di oggetti restituiti,  
  
## <a name="return-value"></a>Valore restituito  
 Il valore HRESULT.