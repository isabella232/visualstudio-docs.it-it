---
title: IDispatchEx::GetDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c466ec767be53d100b970314bf0d81d5dd9dfb20
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097539"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Associa un nome singolo membro al DISPID corrispondente, che può quindi essere utilizzato nelle chiamate successive a `IDispatchEx::InvokeEx`.  
  
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
 Passato nel nome, per eseguire il mapping.  
  
 `grfdex`  
 Determina le opzioni per ottenere l'identificatore di membro. Può trattarsi di una combinazione dei valori seguenti:  
  
|Value|Significato|  
|-----------|-------------|  
|fdexNameCaseSensitive|Richieste che si eseguire la ricerca del nome in modo distinzione maiuscole/minuscole. Può essere ignorata dall'oggetto che non supporta la ricerca tra maiuscole e minuscole.|  
|fdexNameEnsure|Richiede che il membro creato se non esiste già. Il nuovo membro deve essere creato con il valore `VT_EMPTY`.|  
|fdexNameImplicit|Indica che il chiamante è la ricerca di oggetti per un membro di un determinato nome quando l'oggetto di base non viene specificato in modo esplicito.|  
|fdexNameCaseInsensitive|Richieste che si eseguire la ricerca del nome in modo tra maiuscole e minuscole. Può essere ignorata dall'oggetto che non supporta la ricerca tra maiuscole e minuscole.|  
  
 `pid`  
 Puntatore alla posizione allocata dal chiamante per ricevere il risultato DISPID. Se si verifica un errore, `pid` contiene DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|||  
|-|-|  
|`S_OK`|Operazione completata.|  
|`E_OUTOFMEMORY`|Memoria insufficiente.|  
|`DISP_E_UNKNOWNNAME`|Il nome non è stato definito.|  
  
## <a name="remarks"></a>Note  
 `GetDispID` può essere usato al posto di `GetIDsOfNames` per ottenere il DISPID per un determinato membro.  
  
 Poiché `IDispatchEx` consente l'aggiunta e l'eliminazione di membri, il set di DISPID non rimanere costante per la durata di un oggetto.  
  
 Inutilizzata `riid` parametro in `IDispatch::GetIDsOfNames` è stata rimossa.  
  
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