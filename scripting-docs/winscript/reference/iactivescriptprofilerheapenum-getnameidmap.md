---
title: IActiveScriptProfilerHeapEnum::GetNameIdMap | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 88514c93-850b-48d4-9a68-1e27d7411f0d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3284557bf71a038d884c1f8786755b7761770e21
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157386"
---
# <a name="iactivescriptprofilerheapenumgetnameidmap"></a>IActiveScriptProfilerHeapEnum::GetNameIdMap
Restituisce i nomi di stringa corrispondente [tipo PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md) valori.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetNameIdMap (    [out, size_is(,*pcelt)] LPCWSTR* pNameList[],     [out] UINT *pcelt);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pNameList`  
 [out] Matrice di nomi associati [tipo PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md) valori.  
  
 `pcelt`  
 [out] Il numero dei nomi nella matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Il valore HRESULT.