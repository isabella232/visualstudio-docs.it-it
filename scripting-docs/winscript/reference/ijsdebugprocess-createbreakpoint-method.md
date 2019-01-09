---
title: 'Metodo ijsdebugprocess:: CreateBreakpoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 661e584133f4ec3c4e571d157a63844c5b1145b7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097565"
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