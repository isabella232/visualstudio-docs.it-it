---
title: Enumerazione JsDebugReadMemoryFlags | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugReadMemoryFlags
apilocation:
- jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1757678f20a01221ae46e1535d3190cd463d724
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571706"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Enumerazione JsDebugReadMemoryFlags
Flag per specificare il comportamento durante la lettura della memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Members  
  
### <a name="values"></a>Valori  
  
|Name|Descrizione|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Indica che il chiamante desidera che l'operazione di lettura abbia esito positivo se solo una parte della memoria letta è riuscita. Se questa impostazione è impostata, verrà generato un errore E_JsDEBUG_INVALID_MEMORY_ADDRESS solo se ' Address ' non è valido. Se questo flag è chiaro, viene generato un errore E_JsDEBUG_INVALID_MEMORY_ADDRESS se una parte della memoria richiesta è illeggibile.|  
|`None`|Indica che il chiamante desidera il comportamento predefinito per ReadMemory.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)