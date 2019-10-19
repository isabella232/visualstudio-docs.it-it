---
title: 'IActiveScriptAuthor:: GetScriptletTextAttributes | Microsoft Docs'
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
ms.openlocfilehash: 4cd0090b9ade47ad37acf6d285ec7f072f1ea5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576177"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Restituisce gli attributi di testo di un scriptlet.  
  
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
 [in, size_is (`cch`)] Testo scriptlet. Questa stringa non deve essere con terminazione null.  
  
 `cch`  
 in Dimensioni utilizzate per i parametri `pszCode` e `pattr`.  
  
 `pszDelimiter`  
 in Indirizzo del delimitatore di fine del Scriptlet. Quando `pszCode` viene analizzato da un flusso di testo, l'host usa in genere un delimitatore, ad esempio due virgolette singole, per rilevare la fine del Scriptlet. Impostare questo parametro su NULL se non viene usato alcun delimitatore per identificare la fine di scriptlet.  
  
 `dwFlags`  
 in Flag associati agli attributi di testo di scriptlet. Può essere una combinazione dei valori seguenti.  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identificare gli identificatori con l'attributo SOURCETEXT_ATTR_IDENTIFIER e identificare gli operatori punto con l'attributo SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Identificare l'oggetto corrente con l'attributo SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Identificare il contenuto della stringa e il testo del commento con l'attributo SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] Informazioni sul colore per il codice scriptlet.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)    
 @No__t_1 [IActiveScriptAuthor:: GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)  
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)