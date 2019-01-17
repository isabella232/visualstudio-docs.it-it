---
title: Struttura PROFILER_HEAP_OBJECT_SCOPE_LIST | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 114b1a55fce34908c4274877583164aff4ec8dba
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344824"
---
# <a name="profilerheapobjectscopelist-structure"></a>Struttura PROFILER_HEAP_OBJECT_SCOPE_LIST
Questa struttura è associata solo gli oggetti funzione. L'elenco di ambito rappresenta la chiusura per la funzione come un elenco di ambiti in cui ogni ambito è un oggetto heap con un elenco di proprietà associata che rappresenta le variabili in ogni ambito specifico. In alcuni casi, i nomi degli oggetti nell'ambito potrebbe non essere disponibile e solo il relativo indice nell'elenco di proprietà è disponibile.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Tipo|Descrizione|  
|------------|----------|-----------------|  
|count|UINT|Il numero di ambiti|  
|scopes|[Tipo PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Matrice di ambiti.|