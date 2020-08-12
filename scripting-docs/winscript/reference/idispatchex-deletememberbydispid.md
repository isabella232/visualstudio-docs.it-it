---
title: IDispatchEx::D eleteMemberByDispID | Microsoft Docs
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
ms.openlocfilehash: 0c3dbb040e39fd15b77e42b2eaa9fb2cdda0b1b2
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144636"
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
Elimina un membro in base al DISPID.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `id`  
 Identificatore del membro. USA `GetDispID` o `GetNextDispID` per ottenere l'identificatore di invio.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|valore|Significato|
|-|-|  
|`S_OK`|Operazione completata.|  
|`S_FALSE`|Il membro esiste ma non può essere eliminato.|  
  
## <a name="remarks"></a>Osservazioni  
 Se il membro viene eliminato, il DISPID deve rimanere valido per `GetNextDispID` .  
  
 Se un membro con un nome specificato viene eliminato e successivamente viene ricreato un membro con lo stesso nome, il DISPID deve essere lo stesso. (Indipendentemente dal fatto che i nomi dei membri che differiscono solo per le maiuscole e minuscole siano "uguali" sono dipendenti dall'oggetto)  
  
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
 [IDispatchEx:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)