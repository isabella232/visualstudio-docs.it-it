---
title: IActiveScriptAuthor::GetScriptletTextAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8f1b5aac6df8d8659fa323f3f1efcb7721d97f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955058"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Restituisce gli attributi di testo di scriptlet.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszCode`  
 [in, size_is (`cch`)] il testo dello scriptlet. Questa stringa non deve essere con terminazione null.  
  
 `cch`  
 [in] La dimensione utilizzata per la `pszCode` e `pattr` parametri.  
  
 `pszDelimiter`  
 [in] L'indirizzo del delimitatore end-of-scriptlet. Quando si `pszCode` viene analizzata da un flusso di testo, l'host utilizza in genere un delimitatore (ad esempio due virgolette singole), per rilevare la fine dello scriptlet. Impostare questo parametro su NULL se non viene usato alcun delimitatore per identificare la fine dello scriptlet.  
  
 `dwFlags`  
 [in] I flag sono associati gli attributi di testo dello scriptlet. Può essere una combinazione dei valori seguenti.  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identificare gli identificatori che includono l'attributo SOURCETEXT_ATTR_IDENTIFIER e identificare gli operatori di punti che dispongono dell'attributo SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Identificare l'oggetto corrente con l'attributo SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Identificare testo contenuto e il commento della stringa che contiene l'attributo SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] le informazioni sul colore per il codice di scriptlet.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)