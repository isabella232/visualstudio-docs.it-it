---
title: 'Metodo ijsdebugframe:: Getdocumentpositionwithname | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithName
apilocation:
- jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d3b909f3a3ebc672bf6d0a014b519de685b1677
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157308"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>Metodo IJsDebugFrame::GetDocumentPositionWithName
Restituisce la posizione corrente dello stack frame all'interno del documento a livello di utente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pDocumentName`  
 [out] Per gli script statici, un URL al documento. Per gli script dinamici, viene restituito un nome che contiene il tipo di script (ad esempio, codice eval, codice di funzione e così via).  
  
 `pLine`  
 [out] posizione della riga in base 1 all'interno del documento.  
  
 `pColumn`  
 [out] posizione della riga in base 1 all'interno del documento.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)