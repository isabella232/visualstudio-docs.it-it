---
title: 'Metodo ijsdebugframe:: Evaluate | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 574af7823add67a00fc8add922b5e352fa1b369c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091923"
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