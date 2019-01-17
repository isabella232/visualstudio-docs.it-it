---
title: Enumerazione SCRIPTTHREADSTATE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c66d078effd510b3f64cf1f443926984ff2e282
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347671"
---
# <a name="scriptthreadstate-enumeration"></a>Enumerazione SCRIPTTHREADSTATE
Specifica lo stato di un thread in un motore di scripting. Questa enumerazione viene utilizzata per la [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) (metodo).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Thread specificato è attualmente non un evento tramite script, il testo dello script eseguito immediatamente l'elaborazione, di manutenzione o esecuzione di una macro di script.|  
|SCRIPTTHREADSTATE_RUNNING|Thread specificato è attivamente un evento tramite script, il testo dello script eseguito immediatamente l'elaborazione, di manutenzione o esecuzione di una macro di script.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e codici di errore dello script ActiveX](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)