---
title: IActiveScriptAuthor::ParseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c5f9e4969795cedd7da80864c1ad69c0d68f8b9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091806"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Analizza il testo dello script, aggiunge il testo dello script del motore di creazione e crea un `IScriptEntry` oggetto che corrisponde al blocco di script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszCode`  
 [in] Il testo dello script da analizzare.  
  
 `pszItemName`  
 [in] L'indirizzo di buffer che contiene il nome dell'elemento associato al blocco di script.  
  
 `pszDelimiter`  
 [in] L'indirizzo del delimitatore end-di--blocco di script. Quando si `pszCode` viene analizzata da un flusso di testo, l'host utilizza in genere un delimitatore (ad esempio due virgolette singole), per rilevare la fine del blocco di script. Impostare questo parametro su NULL se non è disponibile alcun delimitatore per identificare la fine del blocco di script.  
  
 `dwCookie`  
 [in] Un valore definito dall'applicazione che viene associato al nuovo `IScriptEntry` oggetto.  
  
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