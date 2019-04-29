---
title: Interfaccia IJsDebugStackWalker | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d06af2c509339d9499f66e1f267c54c69951e225
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977812"
---
# <a name="ijsdebugstackwalker-interface"></a>Interfaccia IJsDebugStackWalker
Rappresenta un percorso chiamate dello stack per un thread specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo IJsDebugStackWalker::GetNext](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Ottiene il frame successivo.|  
  
## <a name="remarks"></a>Note  
 Pedoni stack possono essere creati solo quando la destinazione è stato arrestato e non sono valida una volta ripreso anche in questo caso il processo di destinazione.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)