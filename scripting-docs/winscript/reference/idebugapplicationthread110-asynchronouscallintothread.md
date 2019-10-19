---
title: 'IDebugApplicationThread110:: AsynchronousCallIntoThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 06b3031a-4aec-4a47-afaa-04642a4c4870
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 595e73787421b5a5e9ca9407dd174c50451051c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577405"
---
# <a name="idebugapplicationthread110asynchronouscallintothread"></a>IDebugApplicationThread110::AsynchronousCallIntoThread
Esegue una chiamata asincrona al thread principale.  
  
> [!IMPORTANT]
> L' [interfaccia IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) viene implementata da PDM v 11.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pptc`  
 Oggetto [interfaccia IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md) da chiamare.  
  
 `dwParam1`  
 Primo parametro della chiamata.  
  
 `dwParam1`  
 Primo parametro della chiamata.  
  
 `dwParam2`  
 Secondo parametro della chiamata.  
  
 `dwParam3`  
 Terzo parametro della chiamata.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)