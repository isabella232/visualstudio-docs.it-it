---
title: IScriptNode::CreateChildHandler | Microsoft Docs
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
ms.openlocfilehash: bca8b30021d39638f3755bace2625bb38a44242d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787144"
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
 [in] L'indirizzo del nome predefinito per associare lo scriptlet.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] elenco degli identificatori da specificare il nome completo dell'host.  
  
 `cpszNames`  
 [in] Il numero di identificatori nel `prgpszNames` parametro.  
  
 `pszEvent`  
 [in] L'indirizzo del buffer che identifica il nome dell'evento associato allo scriptlet.  
  
 `pszDelimiter`  
 [in] L'indirizzo del delimitatore end-di--blocco di script. Per l'analisi, l'host utilizza in genere un delimitatore (ad esempio due virgolette singole), per rilevare la fine del blocco di script.  
  
 Il delimitatore consente la pre-elaborazione dallo script del motore di creazione. Ad esempio, il motore potrebbe sostituire una virgoletta singola con due virgolette singole da usare come delimitatore. Il motore determina come viene utilizzato il delimitatore.  
  
 Se non viene usato alcun delimitatore per identificare la fine del blocco di script, impostato su NULL.  
  
 `ptiSignature`  
 [in] Le informazioni sul tipo per un oggetto funzione.  
  
 `iMethodSignature`  
 [in] L'indice della funzione di `ITypeInfo``ptiSignature` parametro.  
  
 `isn`  
 [in] L'indice dell'elemento figlio del padre.  
  
 `dwCookie`  
 [in] Un valore definito dall'applicazione che viene usato per associare la voce con l'oggetto host.  
  
 `ppse`  
 [out] L'indirizzo di una variabile che riceve un puntatore al `IScriptEntry` interfaccia dell'istanza figlio.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Scriptlet specifica un gestore eventi. Questo metodo crea un scriptlet se viene chiamato da un `IScriptNode` oggetto che rappresenta una pagina Web. Questo metodo non riesce se viene chiamato da altre interfacce.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)