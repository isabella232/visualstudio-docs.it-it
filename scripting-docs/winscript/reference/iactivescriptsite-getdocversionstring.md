---
title: 'IActiveScriptSite:: GetDocVersionString | Microsoft Docs'
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
ms.openlocfilehash: 8ecc592b6b7fcae5f516a3c1dd111c027e67b6dc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571126"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Recupera una stringa definita dall'host che identifica in modo univoco la versione del documento corrente. Se il documento correlato è stato modificato al di fuori dell'ambito di Windows script (come nel caso di una pagina HTML modificata con blocco note), il motore di scripting può salvare questo insieme allo stato permanente, forzando una ricompilazione alla successiva caricamento dello script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrVersionString`  
 out Indirizzo della stringa di versione del documento definito dall'host.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo oppure `E_NOTIMPL` se questo metodo non è supportato.  
  
## <a name="remarks"></a>Note  
 Se viene restituito `E_NOTIMPL`, il motore di scripting deve presupporre che lo script sia sincronizzato con il documento.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)