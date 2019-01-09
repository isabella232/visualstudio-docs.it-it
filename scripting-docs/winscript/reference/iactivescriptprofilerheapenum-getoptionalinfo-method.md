---
title: 'Metodo iactivescriptprofilerheapenum:: Getoptionalinfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bcba1214a0c57e738dec41cdc4976f478802fedc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088803"
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