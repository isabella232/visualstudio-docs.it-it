---
title: Metodo IActiveScriptProfilerControl5::EnumHeap2 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21661953edbdba2314b88aad5fb55451b06b51a8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097630"
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>Metodo IActiveScriptProfilerControl5::EnumHeap2
Restituisce un'interfaccia ([interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) che può essere utilizzato per scorrere gli oggetti dell'heap GC nel contesto del motore di script associati.  
  
 È possibile chiamare questo metodo in una modalità di debug o modalità di rilascio. Questo metodo deve essere chiamato quando il thread dell'interfaccia utente è inattivo. Dopo aver chiamato il metodo, non devono essere eseguita alcuna operazione in motore di script, ad eccezione [metodo iactivescriptprofilerheapenum:: Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) fino a quando non [metodo iactivescriptprofilerheapenum:: Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)restituisce S_FALSE o il [interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) puntatore a interfaccia viene rilasciato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parametri  
 enumFlags  
 Valore che specifica se le informazioni aggiuntive su un oggetto puntato in una relazione tra oggetti sono visibile. Informazioni aggiuntive possono indicare se l'oggetto puntato è un metodo getter o setter. Per altre informazioni, vedi [enumerazione PROFILER_HEAP_ENUM_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 [out] Restituisce il [interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un HRESULT. I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|L'enumerazione dell'heap completata correttamente.|  
|`E_OUTOFMEMORY`|Non era disponibile memoria sufficiente per eseguire un'enumerazione dell'heap.|  
|`E_FAIL`|Si è verificato un errore interno.|