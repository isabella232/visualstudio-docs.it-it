---
title: 'Metodo ijsdebugprocess:: CreateBreakpoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b398b93c2e7b5ad43abd35d385407b39c0c980f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557972"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>Metodo IJsDebugProcess::CreateBreakPoint
Imposta il punto di interruzione nella posizione del documento specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `documentId`  
 [in] Puntatore a IDebugDocumentText.  
  
 `characterOffset`  
 [in] Offset carattere dall'inizio del file.  
  
 `characterCount`  
 [in] Lunghezza del testo del documento all'interno del quale deve essere inserito il punto di interruzione.  
  
 `isEnabled`  
 [in] Specifica se il punto di interruzione è abilitato.  
  
 `ppDebugBreakPoint`  
 [out] Oggetto che rappresenta il punto di interruzione che è stato creato.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)