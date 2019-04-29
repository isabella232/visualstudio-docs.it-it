---
title: IActiveScriptAuthor::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64df7bd4c0d0dde303cdc15d7111688d14c7dc49
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935458"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Aggiunge un scriptlet di codice come figlio del livello radice `IScriptNode` oggetto. Sull'host, il nome completo dello scriptlet è consentito avere solo due livelli.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszDefaultName`  
 [in] L'indirizzo del nome predefinito per associare lo scriptlet.  
  
 `pszCode`  
 [in] L'indirizzo del testo dello scriptlet.  
  
 `pszItemName`  
 [in] L'indirizzo del buffer dell'identificatore del nome completo di scriptlet nell'host di primo livello.  
  
 `pszSubItemName`  
 [in] L'indirizzo del buffer dell'identificatore del nome completo di scriptlet nell'host del secondo livello. Impostare su NULL se il nome ha un solo livello.  
  
 `pszEventName`  
 [in] L'indirizzo di un buffer che contiene il nome dell'evento per cui lo scriptlet è un gestore eventi.  
  
 `pszDelimiter`  
 [in] L'indirizzo del delimitatore end-di--blocco di script. Quando si `pszCode` viene analizzata da un flusso di testo, l'host utilizza in genere un delimitatore (ad esempio due virgolette singole), per rilevare la fine del blocco di script. Se un delimitatore non contrassegna la fine del blocco di script, impostare questo parametro su NULL.  
  
 `dwCookie`  
 [in] Un valore definito dall'applicazione che viene usato per associare lo scriptlet con un oggetto host.  
  
 `dwFlags`  
 [in] Non utilizzato.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)