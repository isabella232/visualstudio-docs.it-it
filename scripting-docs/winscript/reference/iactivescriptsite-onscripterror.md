---
title: IActiveScriptSite::OnScriptError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d76aa46cbbcdab9a3c5c7b561b91ee58cfcac4ac
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147618"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Comunica all'host che si è verificato un errore di esecuzione mentre il motore è stato eseguito lo script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pase`  
 [in] Indirizzo dell'oggetto di errore [IActiveScriptError](../../winscript/reference/iactivescripterror.md) interfaccia. Un host può utilizzare questa interfaccia per ottenere informazioni relative all'errore di esecuzione.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se l'errore è stato gestito correttamente oppure codice di errore è stato definito in caso contrario, un oggetto OLE.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)