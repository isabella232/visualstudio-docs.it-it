---
title: Enumerazione BREAKPOINT_STATE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKPOINT_STATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKPOINT_STATE enumeration
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: faca5ef7bc89bc16d646f66fb897f1dc44eb831a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955360"
---
# <a name="breakpointstate-enumeration"></a>Enumerazione BREAKPOINT_STATE
Indica lo stato di un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Descrizione|  
|------------|-----------------|  
|BREAKPOINT_DELETED|Il punto di interruzione non esiste più, ma esistono ancora riferimenti a sé stesso.|  
|BREAKPOINT_DISABLED|Il punto di interruzione è presente ma è disabilitato.|  
|BREAKPOINT_ENABLED|Il punto di interruzione esista e sia abilitato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)