---
title: 'IScriptNode:: CreateChildHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e024bb7d6a81b35994edddfe9e71666b0ee8df0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573594"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Aggiunge un scriptlet come istanza figlio di un `IScriptNode`.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszDefaultName`  
 in Indirizzo del nome predefinito da associare a scriptlet.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] Elenco di identificatori dal nome completo nell'host.  
  
 `cpszNames`  
 in Il numero di identificatori nel parametro `prgpszNames`.  
  
 `pszEvent`  
 in Indirizzo del buffer che identifica il nome dell'evento associato a scriptlet.  
  
 `pszDelimiter`  
 in Indirizzo del delimitatore di blocco di fine dello script. Per l'analisi, l'host usa in genere un delimitatore, ad esempio due virgolette singole, per rilevare la fine del blocco di script.  
  
 Il delimitatore consente la pre-elaborazione da parte del motore di creazione degli script. Ad esempio, il motore potrebbe sostituire una virgoletta singola con due virgolette singole da utilizzare come delimitatore. Il motore determina il modo in cui viene utilizzato il delimitatore.  
  
 Impostare su NULL se non viene utilizzato alcun delimitatore per identificare la fine del blocco di script.  
  
 `ptiSignature`  
 in Informazioni sul tipo per un oggetto funzione.  
  
 `iMethodSignature`  
 in Indice della funzione nel parametro `ITypeInfo``ptiSignature`.  
  
 `isn`  
 in Indice dell'elemento figlio nell'elemento padre.  
  
 `dwCookie`  
 in Valore definito dall'applicazione utilizzato per associare la voce all'oggetto host.  
  
 `ppse`  
 out Indirizzo di una variabile che riceve un puntatore all'interfaccia `IScriptEntry` dell'istanza figlio.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Un scriptlet specifica un gestore eventi. Questo metodo crea un scriptlet se viene chiamato da un oggetto `IScriptNode` che rappresenta una pagina Web. Questo metodo non ha esito positivo se viene chiamato da altre interfacce.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)