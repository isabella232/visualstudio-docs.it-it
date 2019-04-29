---
title: Enumerazione BREAKRESUMEACTION | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5c79aacc64eb57282bf09f7e4673980396b37ea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955289"
---
# <a name="breakresumeaction-enumeration"></a>Enumerazione BREAKRESUMEACTION
Descrive come proseguire da un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Descrizione|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|Interrompe l'applicazione.|  
|BREAKRESUMEACTION_CONTINUE|Continua l'esecuzione.|  
|BREAKRESUMEACTION_STEP_INTO|Esegue l'istruzione di una routine.|  
|BREAKRESUMEACTION_STEP_OVER|Ignora una routine.|  
|BREAKRESUMEACTION_STEP_OUT|Esce dalla routine corrente.|  
|BREAKRESUMEACTION_IGNORE|Continua l'esecuzione con lo stato.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|Passa al documento successivo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)