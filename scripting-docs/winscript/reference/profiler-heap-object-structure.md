---
title: Struttura PROFILER_HEAP_OBJECT | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1652c6ebffff88782ffcc879158a5142f22395d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823814"
---
# <a name="profilerheapobject-structure"></a>Struttura PROFILER_HEAP_OBJECT
Rappresenta gli oggetti dell'heap raccolti dal [metodo IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;    union {        PROFILER_HEAP_OBJECT_ID objectId;        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;    USHORT flags;     USHORT optionalInfoCount;} PROFILER_HEAP_OBJECT;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Tipo|Descrizione|  
|------------|----------|-----------------|  
|objectId|[Tipo PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|ID dell'oggetto heap.|  
|externalObjectAddress|[Tipo PROFILER_EXTERNAL_OBJECT_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|L'indirizzo oggetto esterno di un oggetto, ad esempio un oggetto C++ con allocazione, che è all'esterno dell'heap JavaScript.|  
|typeNameId|[Tipo PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|L'ID del nome del tipo di oggetto di heap, recuperato dal [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md). Solo uno dei `externalObjectAddress` oppure `typeName` è presente in base il `flags` valore.|  
|flag|[Enumerazione PROFILER_HEAP_OBJECT_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Flag che contengono informazioni di base sull'oggetto heap.|  
|optionalInfoCount|USHORT|I numerosi [struttura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) record che sono disponibili per l'oggetto heap.|