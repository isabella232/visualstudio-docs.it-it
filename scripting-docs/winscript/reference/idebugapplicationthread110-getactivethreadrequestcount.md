---
title: IDebugApplicationThread110::GetActiveThreadRequestCount | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8bd776aedd4df61797419795afb8dcc8afeb9318
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348191"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Restituisce il numero di richieste di thread da thread del PDM cambio meccanismi che sono in corso. In genere, questo numero è 0 o 1. Tuttavia, il numero può essere maggiore se una chiamata di thread inizia l'elaborazione, ma attiva una chiamata sincrona all'esterno di thread, o in caso contrario, sospende il thread e consente le chiamate in ingresso da elaborare nuovamente (ad esempio, attivando un [ Interfaccia IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md) evento, che viene eseguita sul thread del debugger).  
  
> [!IMPORTANT]
>  [Interfaccia IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) viene implementata da PDM v11.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parametri  
 `puiThreadRequests`  
 [out] Il numero di richieste di thread.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)