---
title: IActiveScriptSite::OnScriptError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d2c9cb95615ad0b978cc7fd9943b687e5a7f3cac
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088413"
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