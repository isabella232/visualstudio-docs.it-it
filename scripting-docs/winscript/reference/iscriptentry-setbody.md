---
title: IScriptEntry::SetBody | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46ebccb57885480d34d79cbd27e99dc6a35b343d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787645"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
Imposta il testo presente nel corpo di un' `IScriptEntry` blocco di script o un `IScriptScriptlet` scriptlet.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `psz`  
 [in] Per un `IScriptEntry` blocco di script, `psz` è il testo racchiuso tra tag di script.  
  
 Per un `IScriptEntry` blocco della funzione, `psz` è il corpo della funzione.  
  
 Per un `IScriptScriptlet` oggetto (che deriva da `IScriptEntry`), `psz` è il testo dello script dello scriptlet.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)