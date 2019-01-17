---
title: IDebugApplicationThread110::IsThreadCallable | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsThreadCallable
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3edf7e8a1495be99d2c5130c307acae92a96b11
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344208"
---
# <a name="idebugapplicationthread110isthreadcallable"></a>IDebugApplicationThread110::IsThreadCallable
Determina se il thread è in uno stato che elabora le chiamate effettuate tramite meccanismi, ad esempio SynchronousCallInThread di passaggio da un thread di PDM.  
  
> [!IMPORTANT]
>  [Interfaccia IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) viene implementata da PDM v11.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pfIsCallable`  
 [out] `true` se il thread è possibile chiamare, in caso contrario `false`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)