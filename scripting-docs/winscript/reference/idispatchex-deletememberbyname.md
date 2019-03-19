---
title: IDispatchEx::DeleteMemberByName | Microsoft Docs
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
ms.openlocfilehash: dc7c8db4ab28e0bd0fcb48f352cb07595f72fd17
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153825"
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
 Determina se il nome del membro viene fatta distinzione tra maiuscole e minuscole. Ciò può essere uno dei valori seguenti:  
  
|Valore|Significato|  
|-----------|-------------|  
|fdexNameCaseSensitive|Richieste che si eseguire la ricerca del nome in modo distinzione maiuscole/minuscole. Può essere ignorato dall'oggetto che non supporta la ricerca tra maiuscole e minuscole.|  
|fdexNameCaseInsensitive|Richieste che si eseguire la ricerca del nome in modo tra maiuscole e minuscole. Può essere ignorato dall'oggetto che non supporta la ricerca tra maiuscole e minuscole.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|||  
|-|-|  
|`S_OK`|Operazione completata.|  
|`S_FALSE`|Membro esiste ma non può essere eliminato.|  
  
## <a name="remarks"></a>Note  
 Se il membro viene eliminato, deve rimanere valido per il DISPID `GetNextDispID`.  
  
 Se un membro con un nome specificato viene eliminato e ricreato in un secondo momento un membro con lo stesso nome, il DISPID deve essere lo stesso. (Se i membri che differiscono solo per i casi sono "uguali" è dipendente dall'oggetto.)  
  
## <a name="example"></a>Esempio  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)