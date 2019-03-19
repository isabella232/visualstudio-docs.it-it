---
title: Struttura DebugStackFrameDescriptor | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fddae48178ec6c56ce647f5c4f3a1bff3d81a980
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153318"
---
# <a name="debugstackframedescriptor-structure"></a>Struttura DebugStackFrameDescriptor
Enumera gli stack frame e unisce l'output da più enumeratori sullo stesso thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>Membri  
 `pdsf`  
 L'oggetto stack frame.  
  
 `dwMin`  
 Rappresentazione dipende dal computer dell'intervallo di indirizzi fisici associati a questo frame dello stack inferiore.  
  
 `dwLim`  
 Rappresentazione dipende dal computer dell'intervallo di indirizzi fisici associati a questo stack frame superiore.  
  
 `fFinal`  
 Flag che indica che il frame viene elaborato.  
  
 `punkFinal`  
 Se questo parametro non è `NULL`, dell'enumeratore corrente unione deve essere interrotta e deve essere avviato uno nuovo. L'oggetto indica come avviare la nuova enumerazione.  
  
## <a name="remarks"></a>Note  
 Il gestore di debug di processi Usa questa struttura per ordinare gli stack frame da più motori di script. Per convenzione, gli stack di aumento delle dimensioni verso il basso. Di conseguenza, nelle architetture in cui gli stack di aumentare, gli indirizzi devono essere complementari a coppie.  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)