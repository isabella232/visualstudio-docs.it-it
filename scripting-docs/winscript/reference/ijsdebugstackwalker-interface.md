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
ms.openlocfilehash: 3b06b8c1f9282c42599c798030440c30450ef6dd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574010"
---
# <a name="ijsdebugstackwalker-interface"></a>Interfaccia IJsDebugStackWalker
Rappresenta un camminatore dello stack per un thread specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Name|Descrizione|  
|----------|-----------------|  
|[Metodo IJsDebugStackWalker::GetNext](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Ottiene il frame successivo.|  
  
## <a name="remarks"></a>Note  
 I Walkers dello stack possono essere creati solo quando la destinazione viene arrestata e non sono validi una volta che il processo di destinazione è stato nuovamente riavviato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)