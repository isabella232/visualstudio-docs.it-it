---
title: Struttura PROFILER_HEAP_OBJECT_OPTIONAL_INFO | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c7f28499b5d6e1e01caab1e6fd83fc5ab72ccf6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151037"
---
# <a name="profilerheapobjectoptionalinfo-structure"></a>Struttura PROFILER_HEAP_OBJECT_OPTIONAL_INFO
Rappresenta informazioni facoltative relative agli oggetti dell'heap.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO{    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union    {        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;    };} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Tipo|Descrizione|  
|------------|----------|-----------------|  
|infoType|[Enumerazione PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Tipo di informazioni facoltative.|  
|prototipo|[Tipo PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|ID dell'oggetto prototipo dell'oggetto heap.|  
|functionName|LPCWSTR|Nome della funzione dell'oggetto heap.|  
|elementAttributesSize|UINT|Le dimensioni degli attributi di elemento dell'oggetto heap.|  
|elementTextChildrenSize|UINT|Le dimensioni degli elementi figlio di testo dell'oggetto heap.|  
|Elencoambiti|[Struttura PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Elenco di ambiti dell'oggetto heap.|  
|internalProperty|[Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Proprietà interna dell'oggetto heap.|  
|namePropertyList|[Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Elenco di proprietà del nome dell'oggetto heap.|  
|indexPropertyList|[Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Elenco di proprietà di indice dell'oggetto heap.|  
|relationshipList|[Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Un elenco delle relazioni dell'oggetto heap.|  
|eventList|[Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Un elenco di eventi dell'oggetto heap.|