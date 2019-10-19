---
title: 'IDispatchEx:: GetDispID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57f0faf6004e2219600f0dbd63749a7e65ca438c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576607"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Esegue il mapping di un nome di singolo membro al DISPID corrispondente, che può quindi essere utilizzato nelle chiamate successive a `IDispatchEx::InvokeEx`.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `bstrName`  
 Passato nome da mappare.  
  
 `grfdex`  
 Determina le opzioni per ottenere l'identificatore del membro. Può trattarsi di una combinazione dei valori seguenti:  
  
|Value|Significato|  
|-----------|-------------|  
|fdexNameCaseSensitive|Richiede che la ricerca del nome venga eseguita con distinzione tra maiuscole e minuscole. Può essere ignorato dall'oggetto che non supporta la ricerca con distinzione tra maiuscole e minuscole.|  
|fdexNameEnsure|Richiede che il membro venga creato se non esiste già. Il nuovo membro deve essere creato con il valore `VT_EMPTY`.|  
|fdexNameImplicit|Indica che il chiamante esegue la ricerca di oggetti per un membro di un nome specifico quando l'oggetto di base non è specificato in modo esplicito.|  
|fdexNameCaseInsensitive|Richiede che la ricerca del nome venga eseguita senza distinzione tra maiuscole e minuscole. Può essere ignorato da un oggetto che non supporta la ricerca senza distinzione tra maiuscole e minuscole.|  
  
 `pid`  
 Puntatore al percorso allocato dal chiamante per ricevere il risultato del DISPID. Se si verifica un errore, `pid` contiene DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|||  
|-|-|  
|`S_OK`|Operazione completata.|  
|`E_OUTOFMEMORY`|Memoria insufficiente.|  
|`DISP_E_UNKNOWNNAME`|Il nome non è noto.|  
  
## <a name="remarks"></a>Note  
 è possibile utilizzare `GetDispID` anziché `GetIDsOfNames` per ottenere il DISPID per un determinato membro.  
  
 Poiché `IDispatchEx` consente l'aggiunta e l'eliminazione di membri, il set di DISPID non rimane costante per la durata di un oggetto.  
  
 Il parametro `riid` non usato in `IDispatch::GetIDsOfNames` è stato rimosso.  
  
## <a name="example"></a>Esempio  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)