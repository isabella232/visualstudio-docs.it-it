---
title: IActiveScriptSite::GetDocVersionString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7327b71329c1f476eab9c27d5e0d5a047664abfa
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147956"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Recupera una stringa definita dall'host che identifica in modo univoco la versione del documento corrente. Se il documento correlato è stato modificato all'esterno dell'ambito dello Script di Windows (come nel caso di una pagina HTML in fase di modifica con il blocco note), il motore di scripting possibile salvare questo oltre allo stato persistente, la volta successiva che viene caricato lo script di ricompilazione forzata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrVersionString`  
 [out] Indirizzo della stringa di versione documento definito dall'host.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` caso di esito positivo o `E_NOTIMPL` se questo metodo non è supportato.  
  
## <a name="remarks"></a>Note  
 Se `E_NOTIMPL` viene restituito, il motore di scripting deve presupporre che lo script sia sincronizzato con il documento.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)