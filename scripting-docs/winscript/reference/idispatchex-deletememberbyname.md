---
title: IDispatchEx::D eleteMemberByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2abb562f65885ee1d12f2ec9b2300fcddd3be37b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576615"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Elimina un membro in base al nome.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parametri  
 `bstrName`  
 Nome del membro da eliminare.  
  
 `grfdex`  
 Determina se il nome del membro fa distinzione tra maiuscole e minuscole. Il valore può essere uno dei seguenti:  
  
|Value|Significato|  
|-----------|-------------|  
|fdexNameCaseSensitive|Richiede che la ricerca del nome venga eseguita con distinzione tra maiuscole e minuscole. Può essere ignorato dall'oggetto che non supporta la ricerca con distinzione tra maiuscole e minuscole.|  
|fdexNameCaseInsensitive|Richiede che la ricerca del nome venga eseguita senza distinzione tra maiuscole e minuscole. Può essere ignorato da un oggetto che non supporta la ricerca senza distinzione tra maiuscole e minuscole.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|||  
|-|-|  
|`S_OK`|Operazione completata.|  
|`S_FALSE`|Il membro esiste ma non può essere eliminato.|  
  
## <a name="remarks"></a>Note  
 Se il membro viene eliminato, il DISPID deve rimanere valido per `GetNextDispID`.  
  
 Se un membro con un nome specificato viene eliminato e successivamente viene ricreato un membro con lo stesso nome, il DISPID deve essere lo stesso. (Indipendentemente dal fatto che i membri che differiscono solo per le maiuscole e minuscole siano "uguali" sono dipendenti dall'oggetto)  
  
## <a name="example"></a>Esempio  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)