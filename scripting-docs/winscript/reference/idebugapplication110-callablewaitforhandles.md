---
title: 'IDebugApplication110:: CallableWaitForHandles | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22af0e9dcf548bbd2f0f8c179b4889d5294eb284
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575083"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Attende che uno qualsiasi degli handle specificati venga segnalato mentre consente di inviare chiamate cross-thread a questo thread. Questo metodo deve essere chiamato dal thread del debugger.  
  
> [!IMPORTANT]
> L' [interfaccia IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) viene implementata da PDM v 11.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Parametri  
 `handleCount`  
 Numero di handle da attendere.  
  
 `pHandles`  
 Set di handle da attendere.  
  
 `pIndex`  
 Quando il valore HRESULT è S_OK, l'indice in `pHandles` per l'handle segnalato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)