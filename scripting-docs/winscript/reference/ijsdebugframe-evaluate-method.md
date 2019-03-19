---
title: 'Metodo ijsdebugframe:: Evaluate | Microsoft Docs'
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
ms.openlocfilehash: b328d6071ae9dc96b8e7f62bad6d4417aa1730f4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157815"
---
# <a name="ijsdebugframeevaluate-method"></a>Metodo IJsDebugFrame::Evaluate
Valutare un'espressione nel contesto di questo frame dello stack.  
  
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
 [in] L'espressione da valutare.  
  
 `ppDebugProperty`  
 [out] Oggetto che rappresenta il Visualizzatore proprietà.  
  
 `pError`  
 [out] Il messaggio di errore, se si verifica un errore.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce quanto segue: S_OK: Esito positivo della valutazione, * ppDebugProperty contiene il risultato della valutazione. S_FALSE: La valutazione genera un errore o l'operazione di valutazione non è supportato, \*pError contiene il messaggio di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)