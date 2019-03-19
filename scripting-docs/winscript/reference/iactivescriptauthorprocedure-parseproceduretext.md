---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c513b105a483d0f80510dff9c91fa2c3f09e0523
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149380"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analizza una routine di codice, aggiunge il testo della stored procedure codice allo script del motore di creazione e crea un `IScriptEntry` oggetto corrispondente alla routine del codice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszCode`  
 [in] Il testo dello script da analizzare.  
  
 `pszFormalParams`  
 [in] L'indirizzo dei nomi di parametro formali per la procedura. I nomi dei parametri devono essere separati dai delimitatori appropriati per lo script del motore di creazione. I nomi non devono essere racchiusi tra parentesi.  
  
 `pszProcedureName`  
 [in] L'indirizzo del nome procedura deve essere analizzato.  
  
 `pszItemName`  
 [in] L'indirizzo del buffer che contiene il nome dell'elemento è associato il `IScriptEntry` oggetto.  
  
 `pszDelimiter`  
 [in] L'indirizzo del delimitatore end-di--blocco di script. Quando si `pszCode` viene analizzata da un flusso di testo, l'host utilizza in genere un delimitatore (ad esempio due virgolette singole), per rilevare la fine del blocco di script. Impostare questo parametro su NULL se non è disponibile alcun delimitatore per contrassegnare la fine del blocco di script.  
  
 `dwCookie`  
 [in] Un valore definito dall'applicazione che viene associato al nuovo `IScriptEntry` oggetto.  
  
 `dwFlags`  
 [in] Non utilizzato.  
  
 `pdispFor`  
 [in] Non utilizzato.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Corrente [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore può neimplementuje metodu questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthorProcedure](../../winscript/reference/iactivescriptauthorprocedure-interface.md)