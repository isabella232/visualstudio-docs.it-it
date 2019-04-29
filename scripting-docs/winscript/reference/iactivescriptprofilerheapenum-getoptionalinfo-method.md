---
title: 'Metodo iactivescriptprofilerheapenum:: Getoptionalinfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab8096b79cfbb91e4b65256c84ab1ba01207d9ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992846"
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>Metodo IActiveScriptProfilerHeapEnum::GetOptionalInfo
Ottiene le informazioni facoltative sull'oggetto specificato (dal set di oggetti heap restituiti dai [metodo IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)).  
  
 Non è necessario liberare la memoria restituita assegnata agli oggetti restituiti. In alternativa, è necessario chiamare il [metodo iactivescriptprofilerheapenum:: Freeobjectandoptionalinfo](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetOptionalInfo (    [in] PROFILER_HEAP_OBJECT* heapObject,    [in] ULONG celt,    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
```  
  
#### <a name="parameters"></a>Parametri  
 `heapObject`  
 Il [struttura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) per cui restituire le informazioni.  
  
 `celt`  
 I numerosi [struttura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) strutture da restituire.  
  
 `optionalInfo`  
 [out] Matrice di [struttura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) strutture per l'oggetto specificato.  
  
## <a name="return-value"></a>Valore restituito  
 Il valore HRESULT.