---
title: SCRIPT_DEBUGGER_OPTIONS Enumeration | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25f74902e2fea451ae5ddaf75d215c3a6c70b050
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155043"
---
# <a name="scriptdebuggeroptions-enumeration"></a>Enumerazione SCRIPT_DEBUGGER_OPTIONS
Indica un set di opzioni e/o funzionalità che si applicano al debugger collegato. Usato nel [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) e [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Queste costanti sono implementate da PDM v 10.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Membri  
  
|Member|Value|Descrizione|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Non sono impostate opzioni.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Indica che l'esecuzione dello script dovrebbe generare eventi BREAKREASON_ERROR quando viene generata un'eccezione. Questa opzione può essere impostata dal debugger, o dal codice utente tramite `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Indica che il debugger collegato supporta web worker.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)