---
title: 'IDebugApplication110:: AsynchronousCallInMainThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::AsynchronousCallInMainThread
ms.assetid: 13b80ff0-4bed-48c1-8031-d4147b51bf6c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04c1a2962662d0046c6b9d323a287d580ee0f3e6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577398"
---
# <a name="idebugapplication110asynchronouscallinmainthread"></a>IDebugApplication110::AsynchronousCallInMainThread
Esegue una chiamata asincrona al thread principale.  
  
> [!IMPORTANT]
> L' [interfaccia IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) viene implementata da PDM v 11.0 e versioni successive. Rilevata in activdbg100.h.  
  
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