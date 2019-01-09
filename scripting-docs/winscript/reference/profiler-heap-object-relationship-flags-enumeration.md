---
title: Enumerazione PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b78285f332b339533d81228de5877043f699a67c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096291"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>Enumerazione PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS
Flag che rappresentano se un oggetto heap puntato in una relazione tra oggetti è un metodo getter o setter. Utilizzato nel [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) metodo quando il valore PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS è specificato nella `enumFlags` parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Valore|Descrizione|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Questo oggetto heap puntato in una relazione tra oggetti non viene identificato come metodo di un getter o setter.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|L'oggetto heap puntato in una relazione tra oggetti è un metodo di richiamo. Queste informazioni verranno archiviate nel livello 2 byte (16 bit) del [profiler_heap_object_relationship](../../winscript/reference/profiler-heap-object-relationship-structure.md) campo.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|L'oggetto heap puntato in una relazione tra oggetti è un metodo setter. Queste informazioni verranno archiviate nel livello 2 byte (16 bit) del `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` campo.|