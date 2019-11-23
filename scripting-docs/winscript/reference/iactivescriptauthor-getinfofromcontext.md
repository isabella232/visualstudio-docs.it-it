---
title: 'IActiveScriptAuthor:: GetInfoFromContext | Microsoft Docs'
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
ms.openlocfilehash: b8b9ad4677d580d495c72866be57712476d6a9c7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985329"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Restituisce le informazioni sul tipo e le posizioni di ancoraggio per un determinato carattere in un blocco di codice. Vengono fornite informazioni per IntelliSense membro, elenchi globali e suggerimenti per i parametri.  
  
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
 in Indirizzo della stringa di blocco di codice utilizzata per generare i risultati delle informazioni.  
  
 `cchCode`  
 in Lunghezza del blocco di codice.  
  
 `ichCurrentPosition`  
 in Posizione del carattere rispetto all'inizio del blocco.  
  
 `dwListTypesRequested`  
 in Tipi di elenco richiesti. Può essere una combinazione dei valori seguenti:  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Nessun elenco.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Elenco dei membri.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Elenco di enumerazione.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Elenco di parametri del metodo di chiamata.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Elenco globale.|  
  
 Il tipo di SCRIPT_CMPL_GLOBALLIST viene considerato come un elemento di completamento predefinito che può essere combinato usando l'operatore OR con altri elementi di completamento. Il motore di creazione script tenta innanzitutto di popolare le informazioni sul tipo per gli altri elementi dell'elenco di completamento. Se l'operazione ha esito negativo, il motore popola per SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 out Tipo di elenco fornito.  
  
 `pichListAnchorPosition`  
 out Indice iniziale del contesto che contiene la posizione corrente. L'indice iniziale è relativo all'inizio del blocco.  
  
 Questa operazione viene popolata solo quando `dwListTypesRequested` include SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST o SCRIPT_CMPL_GLOBALLIST. Per gli altri tipi di elenco richiesti, il risultato è indefinito.  
  
 `pichFuncAnchorPosition`  
 out Indice iniziale della chiamata di funzione che contiene la posizione corrente. L'indice iniziale è relativo all'inizio del blocco.  
  
 Viene popolata solo quando il contesto che contiene la posizione corrente è una chiamata di funzione e quando `dwListTypesRequested` include SCRIPT_CMPL_PARAMLIST. In caso contrario, il risultato è indefinito.  
  
 `pmemid`  
 out MEMBERID della funzione, in base a quanto definito da un tipo nel parametro `IProvideMultipleClassInfo``ppunk` out.  
  
 Questa operazione viene popolata solo quando `dwListTypesRequested` include SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 out Indice del parametro che contiene la posizione corrente. Se la posizione corrente è sul nome della funzione, viene restituito-1.  
  
 Il valore `piCurrentParameter` viene popolato solo quando `dwListTypesRequested` include SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 Informazioni sul tipo, fornite sotto forma di oggetto `IProvideMultipleClassInfo`.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IProvideMultipleClassInfo](/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)   
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)