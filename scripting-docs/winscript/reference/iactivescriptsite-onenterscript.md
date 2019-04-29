---
title: IActiveScriptSite::OnEnterScript | Microsoft Docs
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
ms.openlocfilehash: 5505b30bbfd4e1cbc33022d38d7b7170ffd37dd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992682"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Comunica all'host che il motore di scripting è iniziata l'esecuzione del codice di script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`.  
  
## <a name="remarks"></a>Note  
 Il motore di scripting deve chiamare questo metodo per ogni singola voce o reingresso nel motore di scripting. Ad esempio, se lo script chiama un oggetto che genera un evento come gestito dal motore di script, il motore di scripting deve chiamare `IActiveScriptSite::OnEnterScript` prima di eseguire l'evento e deve chiamare il [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) metodo dopo l'esecuzione dell'evento, ma prima di restituire l'oggetto che ha generato l'evento. Chiamate a questo metodo possono essere annidate. Ogni chiamata a questo metodo richiede una chiamata corrispondente al `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)