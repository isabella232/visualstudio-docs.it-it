---
title: Interfaccia IActiveScriptProfilerHeapEnum | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14562654e0fd3f3567d6f598f84cf2c966b1b8cb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344889"
---
# <a name="iactivescriptprofilerheapenum-interface"></a>Interfaccia IActiveScriptProfilerHeapEnum
Un iteratore sull'heap oggetti associati a un motore di script, raccolto dal [metodo IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## <a name="methods"></a>Metodi  
 [Metodo IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 Ottiene gli oggetti successivo nel set di oggetti degli heap raccolti dal [metodo IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [Metodo IActiveScriptProfilerHeapEnum::GetOptionalInfo](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 Ottiene le informazioni facoltative sull'oggetto specificato nel set di oggetti degli heap raccolti dal [metodo IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [Metodo IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 Libera l'oggetto specificato [struttura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) strutture e i relativi [struttura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) elementi.  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 Restituisce i nomi di stringa corrispondente [tipo PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md) valori...