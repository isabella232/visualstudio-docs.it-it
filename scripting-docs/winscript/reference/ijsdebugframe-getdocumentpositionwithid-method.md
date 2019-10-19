---
title: 'Metodo metodo ijsdebugframe:: GetDocumentPositionWithId | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f35f6fb84db95950fe83d571c9f5e5e7db9de1e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573856"
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>Metodo IJsDebugFrame::GetDocumentPositionWithId
Restituisce la posizione corrente di questo stack frame all'interno del documento a livello di utente.  
  
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
 out ID univoco per un documento di origine (puntatore a IDebugDocumentText).  
  
 `pCharacterOffset`  
 out Offset carattere in base zero dall'inizio dello script.  
  
 `pStatementCharCount`  
 out Lunghezza dell'istruzione corrente, che inizia da * pCharacterOffset, in caratteri.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)