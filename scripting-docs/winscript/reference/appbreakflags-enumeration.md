---
title: Enumerazione APPBREAKFLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 49d9cef3583def8cd23e135b960e46979446b3bb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349023"
---
# <a name="appbreakflags-enumeration"></a>Enumerazione APPBREAKFLAGS
Indicano lo stato corrente del debug delle applicazioni e dei thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Membri  
  
|Member|Value|Descrizione|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Motore del linguaggio deve interrompere immediatamente in tutti i thread con BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Motore del linguaggio deve interrompere immediatamente con BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|Motore del linguaggio deve interrompere immediatamente nel thread di esecuzione di istruzioni con BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|L'applicazione è in esecuzione annidata in un punto di interruzione.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Il debugger è l'esecuzione di istruzioni a livello di origine.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Il debugger è l'esecuzione di istruzioni a livello di codice byte.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Il debugger è l'esecuzione di istruzioni a livello di computer.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Maschera per la separazione di tipi di passaggi.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Un punto di interruzione è in corso.|  
  
## <a name="remarks"></a>Note  
 Alcuni flag di specificare che i motori di linguaggio devono interrompersi alla successiva opportunità, mentre altri flag di specificare la modalità di debug passo a passo del debugger.  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture, enumerazioni e costanti del Debugger dello Script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [Enumerazione BREAKREASON](../../winscript/reference/breakreason-enumeration.md)