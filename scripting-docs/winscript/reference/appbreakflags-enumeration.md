---
title: Enumerazione APPBREAKFLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de6efbc20843fcaa73965334c18cf0e5c2a0abab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572669"
---
# <a name="appbreakflags-enumeration"></a>Enumerazione APPBREAKFLAGS
Indicano lo stato corrente del debug delle applicazioni e dei thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Members  
  
|Member|Value|Descrizione|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Il motore di linguaggio deve interrompersi immediatamente su tutti i thread con BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Il motore di linguaggio deve interrompersi immediatamente con BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|Il motore di linguaggio dovrebbe interrompere immediatamente il thread di esecuzione con BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|L'applicazione è in esecuzione annidata in un punto di interruzione.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Il debugger sta eseguendo un'istruzione a livello di origine.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Il debugger esegue l'istruzione a livello di codice byte.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Il debugger sta eseguendo un'istruzione a livello di computer.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Maschera per scomporre i tipi di passaggio.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|È in corso un punto di interruzione.|  
  
## <a name="remarks"></a>Note  
 Alcuni flag specificano che i motori di linguaggio dovrebbero interrompersi alla successiva opportunità, mentre altri flag specificano la modalità di esecuzione del debugger.  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script activex](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)    
 [Enumerazione BREAKREASON](../../winscript/reference/breakreason-enumeration.md)