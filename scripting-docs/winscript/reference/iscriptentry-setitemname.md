---
title: 'IScriptEntry:: SetItemName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ba226704f5b064c86b52c1b349650d509b2b549
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575361"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Imposta il nome dell'elemento che identifica un oggetto `IScriptEntry`.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `psz`  
 in Indirizzo di un buffer che contiene il nome dell'elemento. Il nome dell'elemento viene utilizzato dall'host per identificare la voce.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Il metodo non è riuscito.|  
  
## <a name="remarks"></a>Note  
 Per `IScriptEntry` oggetti, questo metodo restituisce `S_OK`.  
  
 Per gli oggetti `IScriptScriptlet` (che derivano da `IScriptEntry`), questo metodo restituisce `E_FAIL`. Per `IScriptScriptlet` oggetti, il nome dell'elemento viene impostato da [IActiveScriptAuthor:: AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) e non può essere modificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)    
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)