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
ms.openlocfilehash: 910e08ec6d9982354eb71b50d5e916917808f140
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576544"
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
  
## <a name="members"></a>Members  
 `pdsf`  
 Oggetto stack frame.  
  
 `dwMin`  
 Rappresentazione dipendente dal computer dell'intervallo inferiore di indirizzi fisici associato a questo stack frame.  
  
 `dwLim`  
 Rappresentazione dipendente dal computer dell'intervallo superiore di indirizzi fisici associato a questo stack frame.  
  
 `fFinal`  
 Flag che indica che è in corso l'elaborazione del frame.  
  
 `punkFinal`  
 Se questo parametro non è `NULL`, il merge dell'enumeratore corrente dovrebbe arrestarsi e ne verrà avviato uno nuovo. L'oggetto indica come avviare la nuova enumerazione.  
  
## <a name="remarks"></a>Note  
 Gestione debug processo utilizza questa struttura per ordinare gli stack frame da più motori di script. Per convenzione, la crescita degli stack è inattiva. Di conseguenza, nelle architetture in cui gli stack crescono, gli indirizzi devono essere complementari a due.  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)