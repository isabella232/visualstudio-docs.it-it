---
title: Struttura PROFILER_PROPERTY_TYPE_SUBSTRING_INFO | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3845c872-4302-47b6-8912-7b2d7a3b3357
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 5f873cdf2ebd394e48c1513135f1acdcd700c283
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345643"
---
# <a name="profilerpropertytypesubstringinfo-structure"></a>Struttura PROFILER_PROPERTY_TYPE_SUBSTRING_INFO
Rappresenta le informazioni sul tipo di sottostringa usata nella relazione. Usato nel [struttura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef struct _PROFILER_PROPERTY_TYPE_SUBSTRING_INFO {    UINT length;    LPCWSTR value; } PROFILER_PROPERTY_TYPE_SUBSTRING_INFO;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Tipo|Descrizione|  
|------------|----------|-----------------|  
|length|UINT|L'oggetto è UINT.|  
|predefinito|LPCWSTR|L'oggetto è un LPCWSTR.|