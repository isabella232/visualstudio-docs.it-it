---
title: 'IDebugApplicationThread110:: GetActiveThreadRequestCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e7f038c1d0958701a14899825a2adb0a11cf604d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574483"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Restituisce il numero di richieste di thread dai meccanismi di cambio thread del PDM attualmente in fase di elaborazione. Questo numero è in genere 0 o 1. Tuttavia, il numero può essere maggiore se una chiamata al thread avvia l'elaborazione, ma attiva una chiamata sincrona fuori dal thread, oppure sospende il thread e consente di elaborare di nuovo le chiamate in ingresso, ad esempio attivando un [IRemoteDebugApplicationEvents ](../../winscript/reference/iremotedebugapplicationevents-interface.md)Evento di interfaccia, che viene emesso nel thread del debugger.  
  
> [!IMPORTANT]
> L' [interfaccia IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) viene implementata da PDM v 11.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parametri  
 `puiThreadRequests`  
 out Numero di richieste di thread.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)