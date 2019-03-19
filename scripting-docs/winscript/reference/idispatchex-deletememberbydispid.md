---
title: IDispatchEx::DeleteMemberByDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByDispID method
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36eeeb4c28286bb5712be3908b47a5145e460597
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159231"
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
Elimina un membro da DISPID.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `id`  
 Identificatore del membro. Viene utilizzato `GetDispID` o `GetNextDispID` per ottenere l'ID dispatch.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|||  
|-|-|  
|`S_OK`|Operazione completata.|  
|`S_FALSE`|Membro esiste ma non può essere eliminato.|  
  
## <a name="remarks"></a>Note  
 Se il membro viene eliminato, deve rimanere valido per il DISPID `GetNextDispID`.  
  
 Se un membro con un nome specificato viene eliminato e ricreato in un secondo momento un membro con lo stesso nome, il DISPID deve essere lo stesso. (Se i nomi dei membri che differiscono solo per i casi sono "uguali" è dipendente dall'oggetto.)  
  
## <a name="example"></a>Esempio  
  
```cpp
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)