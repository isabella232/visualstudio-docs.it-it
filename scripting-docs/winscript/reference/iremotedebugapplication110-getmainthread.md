---
title: 'IRemoteDebugApplication110:: GetMainThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetMainThread
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8e4ae024429702f3268a01c1e2e1fb4b40294d8
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985279"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
Restituisce il thread principale per gli host che chiamano il [sito](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). in caso contrario, restituisce E_FAIL.  
  
> [!IMPORTANT]
> L' [interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) viene implementata da PDM v 11.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppThread`  
 out [Interfaccia IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)principale.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)   
 [Interfaccia IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)