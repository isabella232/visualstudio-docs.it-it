---
title: IDebugStackFrame::GetLanguageString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetLanguageString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc20c3ce2f5d198e167b83ffddb65cedc84402d7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087737"
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
Restituisce una descrizione breve o lungo testuale della lingua.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fLong`  
 [in] Flag, dove `TRUE` restituisce una descrizione lunga e `FALSE` restituisce una breve descrizione.  
  
 `pbstrLanguage`  
 [out] La descrizione del linguaggio.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 In genere, se `fLong` è `FALSE`, questo metodo fornisce solo il nome del linguaggio associato al frame dello stack. Quando `fLong` è `TRUE`, questo metodo può fornire una descrizione completa del prodotto.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)