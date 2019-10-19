---
title: Enumerazione BREAKREASON | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f656bdf4e3bc85a014ff8d3011708799aa44bcd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572629"
---
# <a name="breakreason-enumeration"></a>Enumerazione BREAKREASON
Indica la causa dell'interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>Members  
  
|Member|Descrizione|  
|------------|-----------------|  
|BREAKREASON_STEP|Il modulo di gestione del linguaggio è in modalità di esecuzione.|  
|BREAKREASON_BREAKPOINT|Il motore di linguaggio ha rilevato un punto di interruzione esplicito.|  
|BREAKREASON_DEBUGGER_BLOCK|Il modulo di gestione del linguaggio ha rilevato un blocco del debugger in un altro thread.|  
|BREAKREASON_HOST_INITIATED|L'host ha richiesto un'interruzioni.|  
|BREAKREASON_LANGUAGE_INITIATED|Il modulo di gestione del linguaggio ha richiesto un'interruzioni.|  
|BREAKREASON_DEBUGGER_HALT|L'IDE del debugger ha richiesto un'interruzione.|  
|BREAKREASON_ERROR|L'errore è stato causato da un errore di esecuzione.|  
|BREAKREASON_JIT|Causato dall'avvio del debug JIT.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)