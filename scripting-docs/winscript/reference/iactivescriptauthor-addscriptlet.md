---
title: 'IActiveScriptAuthor:: AddScriptlet | Microsoft Docs'
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
ms.openlocfilehash: 3a349a848f282e6b3a228c7b17009e0261801be5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577980"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Aggiunge un scriptlet di codice come figlio dell'oggetto `IScriptNode` a livello radice. Nell'host, il nome completo di scriptlet può avere solo due livelli.  
  
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
 in Indirizzo del nome predefinito da associare a scriptlet.  
  
 `pszCode`  
 in Indirizzo del testo scriptlet.  
  
 `pszItemName`  
 in Indirizzo del buffer dell'identificatore di primo livello del nome completo scriptlet nell'host.  
  
 `pszSubItemName`  
 in Indirizzo del buffer dell'identificatore di secondo livello del nome completo scriptlet nell'host. Impostare su NULL se il nome dispone di un solo livello.  
  
 `pszEventName`  
 in Indirizzo di un buffer che contiene il nome dell'evento per il quale scriptlet è un gestore eventi.  
  
 `pszDelimiter`  
 in Indirizzo del delimitatore di blocco di fine dello script. Quando `pszCode` viene analizzato da un flusso di testo, l'host usa in genere un delimitatore, ad esempio due virgolette singole, per rilevare la fine del blocco di script. Impostare questo parametro su NULL se un delimitatore non contrassegna la fine del blocco di script.  
  
 `dwCookie`  
 in Valore definito dall'applicazione utilizzato per associare scriptlet a un oggetto host.  
  
 `dwFlags`  
 in Non utilizzato.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)