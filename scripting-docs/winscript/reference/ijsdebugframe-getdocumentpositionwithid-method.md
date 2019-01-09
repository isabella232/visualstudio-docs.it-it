---
title: 'Metodo ijsdebugframe:: Getdocumentpositionwithid | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithId
apilocation:
- jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c37f31ca6b75ca826dbdab93847a1e70ff054c1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090012"
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>Metodo IJsDebugFrame::GetDocumentPositionWithId
Restituisce la posizione corrente dello stack frame all'interno del documento a livello di utente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetDocumentPositionWithId(  
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
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)