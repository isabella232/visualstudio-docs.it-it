---
title: 'Metodo ijsdebugbreakpoint:: Getdocumentposition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.GetDocumentPosition
apilocation:
- jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 146eb26c887cd24d1eb7af858535fcecac62b41d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583145"
---
# <a name="ijsdebugbreakpointgetdocumentposition-method"></a>Metodo IJsDebugBreakPoint::GetDocumentPosition
Restituisce la posizione dell'istruzione in cui è stata associata al punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetDocumentPosition(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pDocumentId`  
 [out] ID univoco per un documento di origine (puntatore a IDebugDocumentText).  
  
 `pCharacterOffset`  
 [out] L'offset carattere in base zero dall'inizio dello script.  
  
 `pStatementCharCount`  
 [out] La lunghezza dell'istruzione corrente, che inizia a * pCharacterOffset, in caratteri.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)