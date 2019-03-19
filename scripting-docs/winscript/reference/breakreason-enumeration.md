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
ms.openlocfilehash: 939d9f36c9838f02e58bc433d1a7bb9bef43c28d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160589"
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
  
## <a name="members"></a>Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|BREAKREASON_STEP|Il motore del linguaggio è nella modalità di debug passo a passo.|  
|BREAKREASON_BREAKPOINT|Il motore del linguaggio ha rilevato un punto di interruzione esplicito.|  
|BREAKREASON_DEBUGGER_BLOCK|Il motore del linguaggio ha rilevato un blocco di debugger su un altro thread.|  
|BREAKREASON_HOST_INITIATED|L'host ha richiesto un'interruzione.|  
|BREAKREASON_LANGUAGE_INITIATED|Il motore del linguaggio ha richiesto un'interruzione.|  
|BREAKREASON_DEBUGGER_HALT|L'IDE di debug ha richiesto un'interruzione.|  
|BREAKREASON_ERROR|Un errore di esecuzione ha causato l'interruzione.|  
|BREAKREASON_JIT|Causati da Avvio debug JIT.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)