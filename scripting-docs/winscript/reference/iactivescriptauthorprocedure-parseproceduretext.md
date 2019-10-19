---
title: IActiveScriptAuthorProcedure::P arseProcedureText | Microsoft Docs
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
ms.openlocfilehash: 11a34843f30274ec78f1652c5ed5cd4dbcf2884a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572822"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analizza una routine di codice, aggiunge il testo della procedura di codice al motore di creazione degli script e crea un `IScriptEntry` oggetto che corrisponde alla routine di codice.  
  
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
 in Testo dello script da analizzare.  
  
 `pszFormalParams`  
 in Indirizzo dei nomi dei parametri formali per la procedura. I nomi dei parametri devono essere separati dai delimitatori appropriati per il motore di creazione degli script. I nomi non devono essere racchiusi tra parentesi.  
  
 `pszProcedureName`  
 in Indirizzo del nome della stored procedure da analizzare.  
  
 `pszItemName`  
 in Indirizzo del buffer che contiene il nome dell'elemento associato all'oggetto `IScriptEntry`.  
  
 `pszDelimiter`  
 in Indirizzo del delimitatore di blocco di fine dello script. Quando `pszCode` viene analizzato da un flusso di testo, l'host usa in genere un delimitatore, ad esempio due virgolette singole, per rilevare la fine del blocco di script. Impostare questo parametro su NULL se non è presente alcun delimitatore per contrassegnare la fine del blocco di script.  
  
 `dwCookie`  
 in Valore definito dall'applicazione associato al nuovo oggetto `IScriptEntry`.  
  
 `dwFlags`  
 in Non utilizzato.  
  
 `pdispFor`  
 in Non utilizzato.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Il motore di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] corrente non implementa questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthorProcedure](../../winscript/reference/iactivescriptauthorprocedure-interface.md)