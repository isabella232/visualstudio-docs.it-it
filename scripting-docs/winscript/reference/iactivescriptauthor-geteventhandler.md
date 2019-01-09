---
title: IActiveScriptAuthor::GetEventHandler | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2e7f6cc265815db4acd847270b28c3e744257fa0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086684"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Restituisce lo scriptlet che ha gli attributi specificati.  
  
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
 [in] Il `IDispatch` oggetto che corrisponde alla `NamedItem` al quale è associato lo scriptlet.  
  
 `pszItem`  
 [in] L'indirizzo del buffer dell'identificatore del nome completo di scriptlet nell'host di primo livello.  
  
 `pszSubItem`  
 [in] L'indirizzo del buffer dell'identificatore del nome completo di scriptlet nell'host del secondo livello. Impostare su NULL se il nome ha un solo livello.  
  
 `pszEvent`  
 [in] L'indirizzo di un buffer che contiene il nome dell'evento. Lo scriptlet è un gestore eventi per questo evento.  
  
 `ppse`  
 [out] L'indirizzo di una variabile che riceve un puntatore al `IScriptEntry` interfaccia dello scriptlet che ha gli attributi specificati.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)