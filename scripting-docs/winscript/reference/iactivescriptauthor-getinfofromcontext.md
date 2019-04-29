---
title: IActiveScriptAuthor::GetInfoFromContext | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetInfoFromContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4fe885e116019608dd8d748c3cbdaff5d31dd2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935386"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Restituisce digitare le informazioni e le posizioni di ancoraggio per un determinato carattere in un blocco di codice. Fornisce informazioni per il membro IntelliSense, gli elenchi globali e suggerimenti relativi ai parametri.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszCode`  
 [in] L'indirizzo della stringa blocco di codice utilizzata per generare i risultati di informazioni.  
  
 `cchCode`  
 [in] La lunghezza del blocco di codice.  
  
 `ichCurrentPosition`  
 [in] Posizione del carattere relativo all'inizio del blocco.  
  
 `dwListTypesRequested`  
 [in] I tipi di elenco richiesti. Può essere una combinazione dei valori seguenti:  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Nessun elenco.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Elenco dei membri.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Elenco di enumerazione.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Chiamare l'elenco di parametri di metodo.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Elenco globale.|  
  
 Il tipo SCRIPT_CMPL_GLOBALLIST viene considerato come un elemento di completamento predefinito che può essere combinato utilizzando l'operatore OR con altri elementi di completamento. Lo script di creazione motore innanzitutto tenta di popolare le informazioni sul tipo per gli altri elementi dell'elenco di completamento. Se il problema persiste, il motore compila per SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 [out] Il tipo di elenco specificato.  
  
 `pichListAnchorPosition`  
 [out] Indice iniziale del contesto che contiene la posizione corrente. L'indice iniziale è relativo all'inizio del blocco.  
  
 Questo campo viene popolato solo quando `dwListTypesRequested` include SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST o SCRIPT_CMPL_GLOBALLIST. Per altri tipi di elenco richiesto, il risultato è indefinito.  
  
 `pichFuncAnchorPosition`  
 [out] Indice iniziale della chiamata di funzione che contiene la posizione corrente. L'indice iniziale è relativo all'inizio del blocco.  
  
 Questo campo viene popolato solo quando il contesto che contiene la posizione corrente è una chiamata di funzione e quando `dwListTypesRequested` include SCRIPT_CMPL_PARAMLIST. In caso contrario, il risultato è indefinito.  
  
 `pmemid`  
 [out] La proprietà MEMBERID della funzione, come definito da un tipo nel `IProvideMultipleClassInfo``ppunk` parametro out.  
  
 Questo campo viene popolato solo quando `dwListTypesRequested` include SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 [out] L'indice del parametro che contiene la posizione corrente. Se la posizione corrente è sul nome della funzione, viene restituito -1.  
  
 Il `piCurrentParameter` valore viene popolato solo quando `dwListTypesRequested` include SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 Le informazioni sul tipo, che viene forniti sotto forma di un `IProvideMultipleClassInfo` oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IProvideMultipleClassInfo](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)   
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)