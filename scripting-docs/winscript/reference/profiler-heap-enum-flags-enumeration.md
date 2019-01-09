---
title: Enumerazione PROFILER_HEAP_ENUM_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c711dd3a4174f38bf2f3b3e163805e6cfa1c314
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091832"
---
# <a name="profilerheapenumflags-enumeration"></a>Enumerazione PROFILER_HEAP_ENUM_FLAGS
Flag che rappresentano se le informazioni aggiuntive su un oggetto heap puntano in una relazione tra oggetti è esposto. Utilizzato nel [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) (metodo).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,} PROFILER_HEAP_ENUM_FLAGS;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Valore|Descrizione|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_ENUM_FLAGS_NONE|0x00000000|Questo oggetto heap non espone informazioni aggiuntive su una relazione tra oggetti. Questo oggetto heap si comporta nello stesso modo [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER_HEAP_ENUM_ENUM_ STORE_RELATIONSHIP_FLAGS|0x00000001|Questo oggetto heap esporrà informazioni o meno un oggetto puntato in una relazione tra oggetti è un metodo getter o setter. Queste informazioni verranno archiviate nel livello 2 byte (16 bit) del [profiler_heap_object_relationship](../../winscript/reference/profiler-heap-object-relationship-structure.md) campo tra il [PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) valori di enumerazione.|  
|PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|0x00000002|Questo oggetto heap viene usato per visualizzare correttamente la sottostringa.|  
|PROFILER_HEAP_ENUM_FLAGS_RELATIONSHIP_SUBSTRINGS|PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS &AMP;#124; PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|Questo oggetto heap viene usato per visualizzare correttamente la sottostringa.|