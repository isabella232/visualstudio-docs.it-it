---
title: 'Metodo metodo ijsdebugframe:: Evaluate | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6227b97c1fd5fae32db3e13ef72751726c36b043
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573489"
---
# <a name="ijsdebugframeevaluate-method"></a>Metodo IJsDebugFrame::Evaluate
Valutare un'espressione nel contesto di questo stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pExpressionText`  
 in Espressione da valutare.  
  
 `ppDebugProperty`  
 out Oggetto che rappresenta il Visualizzatore proprietà.  
  
 `pError`  
 out Messaggio di errore, se si verifica un errore.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce quanto segue: S_OK: la valutazione ha esito positivo, * ppDebugProperty contiene il risultato della valutazione. S_FALSE: la valutazione genera un errore (oppure l'operazione di valutazione non è supportata), \*pError contiene il messaggio di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)