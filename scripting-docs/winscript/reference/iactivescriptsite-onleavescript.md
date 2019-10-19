---
title: 'IActiveScriptSite:: OnLeaveScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9d872948fea14998f9c6f8140467d6e4c83d056
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570325"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informa l'host che il motore di scripting ha restituito l'esecuzione del codice di script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`.  
  
## <a name="remarks"></a>Note  
 Il motore di scripting deve chiamare questo metodo prima di restituire il controllo a un'applicazione chiamante che è entrata nel motore di scripting. Se, ad esempio, lo script chiama un oggetto che quindi genera un evento gestito dal motore di scripting, il motore di scripting deve chiamare il metodo [IActiveScriptSite:: OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) prima di eseguire l'evento e deve chiamare `IActiveScriptSite::OnLeaveScript` dopo l'esecuzione dell'evento. prima di tornare all'oggetto che ha generato l'evento. Le chiamate a questo metodo possono essere nidificate. Ogni chiamata a `IActiveScriptSite::OnEnterScript` richiede una chiamata corrispondente a questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)