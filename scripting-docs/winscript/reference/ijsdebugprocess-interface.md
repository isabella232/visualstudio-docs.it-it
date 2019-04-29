---
title: Interfaccia IJsDebugProcess | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 411679a03daf27046fdcede7ff48e76212bbd2fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557946"
---
# <a name="ijsdebugprocess-interface"></a>Interfaccia IJsDebugProcess
Fornisce le routine per controllare e analizzare il processo di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint Method](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Imposta il punto di interruzione nella posizione del documento specificata.|  
|[Metodo IJsDebugProcess::CreateStackWalker](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Metodo factory per chiamate nello stack.|  
|[Metodo IJsDebugProcess::PerformAsyncBreak](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Inserisce il motore di script in modalità di interruzione facendo in modo che in modo da interrompere successiva istruzione di script.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)