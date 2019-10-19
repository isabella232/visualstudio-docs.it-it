---
title: 'IActiveScriptAuthor:: GetEventHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69b32f0040ea6d52e0712b8e1813cc5a0b40c58
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576221"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Restituisce l'oggetto scriptlet con gli attributi specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdisp`  
 in Oggetto `IDispatch` che corrisponde al `NamedItem` a cui è associato il scriptlet.  
  
 `pszItem`  
 in Indirizzo del buffer dell'identificatore di primo livello del nome completo scriptlet nell'host.  
  
 `pszSubItem`  
 in Indirizzo del buffer dell'identificatore di secondo livello del nome completo scriptlet nell'host. Impostare su NULL se il nome dispone di un solo livello.  
  
 `pszEvent`  
 in Indirizzo di un buffer che contiene il nome dell'evento. Scriptlet è un gestore eventi per questo evento.  
  
 `ppse`  
 out Indirizzo di una variabile che riceve un puntatore all'interfaccia `IScriptEntry` di scriptlet con gli attributi specificati.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)    
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)