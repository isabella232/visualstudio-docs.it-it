---
title: 'Metodo metodo ijsdebugframe:: GetDocumentPositionWithName | Microsoft Docs'
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
ms.openlocfilehash: b818ca4dc1ec4402973026668972507861c86f22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575114"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>Metodo IJsDebugFrame::GetDocumentPositionWithName
Restituisce la posizione corrente di questo stack frame all'interno del documento a livello di utente.  
  
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
 out Per gli script statici, un URL da documentare. Per gli script dinamici, viene restituito un nome contenente il tipo di script, ad esempio il codice eval, il codice della funzione e così via.  
  
 `pLine`  
 [out] posizione della riga in base 1 all'interno del documento.  
  
 `pColumn`  
 [out] posizione della riga in base 1 all'interno del documento.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)