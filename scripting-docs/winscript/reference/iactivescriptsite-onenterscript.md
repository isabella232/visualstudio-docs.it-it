---
title: 'IActiveScriptSite:: OnEnterScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26e4f221014d90478bbbc7bb5771276706c764c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570356"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informa l'host che il motore di script ha iniziato l'esecuzione del codice di script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`.  
  
## <a name="remarks"></a>Note  
 Il motore di scripting deve chiamare questo metodo per ogni voce o reimmissione nel motore di scripting. Se, ad esempio, lo script chiama un oggetto che quindi genera un evento gestito dal motore di scripting, il motore di scripting deve chiamare `IActiveScriptSite::OnEnterScript` prima di eseguire l'evento e deve chiamare il metodo [IActiveScriptSite:: OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) dopo l'esecuzione dell'evento. ma prima di tornare all'oggetto che ha generato l'evento. Le chiamate a questo metodo possono essere nidificate. Ogni chiamata a questo metodo richiede una chiamata corrispondente a `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)