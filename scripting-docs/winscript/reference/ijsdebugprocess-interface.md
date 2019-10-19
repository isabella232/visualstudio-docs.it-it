---
title: Interfaccia metodo ijsdebugprocess | Microsoft Docs
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
ms.openlocfilehash: 9200515b2c975fb1fa5b2acda7c261cb684d85b4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577339"
---
# <a name="ijsdebugprocess-interface"></a>Interfaccia IJsDebugProcess
Fornisce le routine per controllare e controllare il processo di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Name|Descrizione|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint Method](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Imposta il punto di interruzione nella posizione del documento specificata.|  
|[Metodo IJsDebugProcess::CreateStackWalker](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Metodo Factory per stack Walker.|  
|[Metodo IJsDebugProcess::PerformAsyncBreak](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Inserisce il modulo di gestione di script in modalità di interruzioni, causando interruzioni nella successiva istruzione di script.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)