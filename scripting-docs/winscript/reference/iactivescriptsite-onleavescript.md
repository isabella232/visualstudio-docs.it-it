---
title: IActiveScriptSite::OnLeaveScript | Microsoft Docs
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
ms.openlocfilehash: da39058a8f069c4799835108372d11849d86444e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992670"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Comunica all'host che il motore di script ha restituito dall'esecuzione di codice di script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`.  
  
## <a name="remarks"></a>Note  
 Il motore di scripting deve chiamare questo metodo prima di restituire il controllo a un'applicazione chiamante che il motore di script immessi. Ad esempio, se lo script chiama un oggetto che genera un evento come gestito dal motore di script, il motore di scripting deve chiamare il [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) metodo prima di eseguire l'evento e deve chiamare `IActiveScriptSite::OnLeaveScript`dopo l'esecuzione dell'evento prima di restituire l'oggetto che ha generato l'evento. Chiamate a questo metodo possono essere annidate. Ogni chiamata a `IActiveScriptSite::OnEnterScript` richiede una chiamata corrispondente a questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)