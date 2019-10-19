---
title: 'IScriptEntry:: sebody | Microsoft Docs'
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
ms.openlocfilehash: 1af865c8366481204ee413377a083b09d8c97383
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575385"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
Imposta il testo che si trova nel corpo di un `IScriptEntry` blocco di script o di un `IScriptScriptlet` scriptlet.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `psz`  
 in Per un blocco di script `IScriptEntry`, `psz` è il testo racchiuso tra tag di script.  
  
 Per un blocco di funzione `IScriptEntry`, `psz` è il corpo della funzione.  
  
 Per un oggetto `IScriptScriptlet` (che deriva da `IScriptEntry`), `psz` è il testo dello script di scriptlet.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)    
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)