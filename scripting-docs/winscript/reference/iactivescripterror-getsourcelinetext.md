---
title: IActiveScriptError::GetSourceLineText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourceLineText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourceLineText
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 702f1655b244116e1bb7dca3d5fc90de3d1f5bdf
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155823"
---
# <a name="iactivescripterrorgetsourcelinetext"></a>IActiveScriptError::GetSourceLineText
Recupera la riga nel file di origine in cui cui si è verificato un errore durante l'esecuzione di uno script di un motore di scripting.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## <a name="parameter"></a>Parametro  
 `pbstrSourceLine`  
 [out] Indirizzo di un buffer che riceve la riga del codice sorgente in cui si è verificato l'errore.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` caso di esito positivo o `E_FAIL` se non è stata recuperata la riga nel file di origine.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)