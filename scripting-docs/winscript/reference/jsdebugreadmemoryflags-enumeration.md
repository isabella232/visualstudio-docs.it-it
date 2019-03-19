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
ms.openlocfilehash: c908fdbf17b13b84355dff208b7f3106bfc72087
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156411"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Enumerazione JsDebugReadMemoryFlags
Flag per specificare il comportamento durante la lettura della memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="values"></a>Valori  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Indica che il chiamante desidera che l'operazione di lettura abbia esito positivo se solo parte della memoria di lettura ha esito positivo. Se è impostato, verrà generato un errore E_JsDEBUG_INVALID_MEMORY_ADDRESS solo se "Indirizzo" non è valido. Se questo flag è cancellato, verrà generato un errore E_JsDEBUG_INVALID_MEMORY_ADDRESS se qualsiasi parte della memoria richiesta è illeggibile.|  
|`None`|Indica che il chiamante desidera il comportamento predefinito per ReadMemory.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)